<template>
  <div class="main">
    <div class="filter">
      <Filter @selectedCity="sendSelectedCity" />
    </div>
    <div class="cards">
      <FilterBar @sortValue="sortValue" />
      <CardContainer
        :searching="searching"
        :selectedCity="selectedCity"
        :sortedValue="sorting"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, ref } from "vue";
import Filter from "./Filter.vue";
import FilterBar from "./FilterBar.vue";
import CardContainer from "./CardContainer.vue";

defineProps({
  searching: String,
});

const selectedCity = ref();
const sorting = ref();

const sendSelectedCity = (city: []) => {
  if (city) {
    selectedCity.value = city;
  }
  console.log("main: ", selectedCity.value);
};

const sortValue = (sortingValue: string) => {
  sorting.value = sortingValue;
};
</script>

<style scoped>
.main {
  display: flex;
  padding: 1.5rem;
  padding-left: 9.75rem;
}
.filter {
  width: 15rem;
  height: 30rem;
}

.cards {
  width: 100%;
  padding: 0 1rem;
}

@media only screen and (max-width: 576px) {
  .main {
    display: block;
    padding-left: 1rem;
  }

  .filter {
    width: 100%;
    height: 15rem;
    margin-bottom: 0.5rem;
  }

  .cards {
    width: 100%;
    padding: 0;
  }
}

@media only screen and (min-width: 576px) and (max-width: 768px) {
  .main {
    display: block;
    padding-left: 1rem;
  }

  .filter {
    width: 100%;
    height: 15rem;
    margin-bottom: 0.5rem;
  }

  .cards {
    width: 100%;
    padding: 0;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .main {
    display: block;
    padding-left: 1rem;
  }

  .filter {
    width: 100%;
    height: 15rem;
    margin-bottom: 0.5rem;
  }

  .cards {
    width: 100%;
    padding: 0;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .main {
    display: block;
    padding-left: 1rem;
  }

  .filter {
    width: 100%;
    height: 15rem;
    margin-bottom: 0.5rem;
  }

  .cards {
    width: 100%;
    padding: 0;
  }
}

@media only screen and (min-width: 993px) and (max-width: 1200px) {
  .main {
    display: flex;
    padding: 1.5rem;
    padding-left: 1rem;
  }
  .filter {
    width: 15rem;
    height: 30rem;
  }

  .cards {
    width: 100%;
    padding: 0 1rem;
  }
}
</style>
