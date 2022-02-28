<!-- <template>
  <div class="filter">
    <div>Por Estado</div>
    <div class="selecting">
      <input type="checkbox" title="Sao Paulo" /><span class="title"
        >Sao Paulo</span
      >
    </div>
    <div class="selecting">
      <input type="checkbox" title="Sao Paulo" /><span class="title"
        >Rio de Janeiro</span
      >
    </div>
    <div class="selecting">
      <input type="checkbox" title="Sao Paulo" /><span class="title"
        >Minas Gerais</span
      >
    </div>
    <div class="selecting">
      <input type="checkbox" title="Sao Paulo" /><span class="title"
        >Espirito Santo</span
      >
    </div>
    <div class="selecting">
      <input type="checkbox" title="Sao Paulo" /><span class="title"
        >Bahia</span
      >
    </div>
    <div class="selecting">Ver Todos</div>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.filter {
  width: 17rem;
  height: 30rem;
  margin: 2.5rem 1rem 0 9.5rem;
  border: 1px solid #e5e5e5;
  border-radius: 0.25rem;
  font-family: "Roboto", sans-serif;
}

.filter div {
  font-weight: 900;
  margin: 1.5rem;
}

.filter .title {
  font-size: 0.8rem;
}

.selecting {
  display: flex;
  align-items: center;
}
</style> -->

<template>
  <div class="filter">
    <div class="title">Por Estado</div>

    <div>
      <ul class="checkboxes-list">
        <li v-for="(city, index) in citiesData" :key="index">
          <input
            type="checkbox"
            :value="city"
            v-model="cities"
            @change="updateCheckall()"
          />{{ city }}
        </li>
      </ul>
      <input type="checkbox" @click="checkAll()" v-model="isCheckAll" /> Select
      All
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, defineEmits } from "vue";

const emit = defineEmits(["selectedCity"]);

const citiesData = ref<string[]>([
  "Sao Paulo",
  "Rio de Janeiro",
  "Minas Gerais",
  "Espirito Santo",
  "Bahia",
]);
const isCheckAll = ref(false);
const cities = ref<string[]>([]);

const checkAll = () => {
  isCheckAll.value = !isCheckAll.value;
  cities.value = [];
  if (isCheckAll.value) {
    for (let key in citiesData.value) {
      cities.value.push(citiesData.value[key]);
    }
    emit("selectedCity", cities.value);
  } else {
    emit("selectedCity", []);
  }
};

const updateCheckall = () => {
  if (cities.value.length == citiesData.value.length) {
    isCheckAll.value = true;
  } else {
    isCheckAll.value = false;
  }
  emit("selectedCity", cities.value);
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.filter {
  width: 100%;
  height: 30rem;
  padding: 1rem;
  border: 1px solid #e5e5e5;
  border-radius: 0.25rem;
  font-family: "Roboto", sans-serif;
}

.title {
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
}

.selecting {
  display: flex;
  align-items: center;
}

.checkboxes-list {
  list-style: none;
}
</style>
