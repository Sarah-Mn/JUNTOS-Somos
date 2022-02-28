<template>
  <div class="card-container" v-if="!showLoading">
    <div v-for="(people, index) in peoplePerPage" :key="index">
      <Card :people="people" />
    </div>
  </div>

  <div class="card-container" v-if="showLoading">
    <div v-for="n in 9" :key="n">
      <CardSkeleton />
    </div>
  </div>

  <div class="pagination-container">
    <Pagination
      :totalPages="totalPages"
      :perPage="perPage"
      :currentPage="currentPage"
      @pagechanged="onPageChange"
    />
  </div>
</template>

<script lang="ts" setup>
import Card from "./Card.vue";
import CardSkeleton from "./CardSkeleton.vue";
import { onMounted, ref, defineProps, computed, onUpdated } from "vue";
import Pagination from "./Pagination.vue";
import axios from "axios";

const props = defineProps({
  searching: String,
  selectedCity: Array,
  sortedValue: String,
  selectAllCity: Array,
});

const peoples = ref([]);
const currentPage = ref(1);
const totalPages = ref();
const perPage = ref(9);
const showLoading = ref(true);
const peoplePerPage = ref<Record<string, unknown>[]>([]);
const index = ref(0);
const offSet = ref(9);

const onPageChange = (page: number) => {
  currentPage.value = page;
  peoplePerPage.value = [];

  if (page === 1 || page <= 0) {
    index.value = 0;
    offSet.value = perPage.value;
  } else if (page > peoples.value.length) {
    index.value = page - 1;
    offSet.value = peoples.value.length;
  } else {
    index.value = page * perPage.value - perPage.value;
    offSet.value = index.value + perPage.value;
  }

  peoplePerPage.value = peoples.value.slice(index.value, offSet.value);
};

onMounted(async () => {
  await axios
    .get("/results.json")
    .then((res) => {
      peoples.value = res.data.results;
    })
    .catch((err) => {
      console.error(err);
    });

  totalPages.value = peoples.value.length / 10;
  peoplePerPage.value = peoples.value.slice(0, 9);

  showLoading.value = false;
});

onUpdated(() => {
  if (props.searching) {
    const searchedProducts = computed(() => {
      return peoples.value.filter((people: any) => {
        return (
          people.name.first
            .toLowerCase()
            .indexOf(props.searching?.toLowerCase()) != -1
        );
      });
    });
    peoplePerPage.value = searchedProducts.value;

    return peoplePerPage.value;
  } else {
    peoplePerPage.value = peoples.value.slice(index.value, offSet.value);
  }

  if (props.selectedCity) {
    const valObj = ref([]);
    const cities = props.selectedCity.map((city: any) => {
      valObj.value = peoples.value.filter((elem: any) => {
        if (elem.location.state.toLowerCase() === city.toLowerCase()) {
          return elem;
        }
      });
      return valObj.value;
    });

    peoplePerPage.value = cities.flat();
  }

  if (props.selectedCity?.length === 0) {
    peoplePerPage.value = peoples.value.slice(index.value, offSet.value);
  }

  if (props.sortedValue) {
    if (props.sortedValue === "name") {
      return peoplePerPage.value.sort((a: any, b: any) =>
        a.name.first > b.name.first ? 1 : -1
      );
    }

    if (props.sortedValue === "state") {
      return peoplePerPage.value.sort((a: any, b: any) =>
        a.location.state > b.location.state ? 1 : -1
      );
    }
  }
});
</script>

<style scoped>
.card-container {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}

@media only screen and (max-width: 576px) {
  .pagination-container {
    width: 100%;
    margin: 0 auto;
  }

  .card-container {
    width: 100%;
    justify-content: center;
  }
}

@media only screen and (min-width: 576px) and (max-width: 768px) {
  .card-container {
    width: 100%;
    justify-content: center;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .card-container {
    width: 100%;
    justify-content: center;
  }
}
</style>
