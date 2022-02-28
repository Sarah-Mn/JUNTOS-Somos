<template>
  <div class="filter-bar">
    <div class="items-number">Exibindo 9 de 200 itens</div>
    <div class="sort-section" @click="sendSortValue">
      <label for="sortOption">Ordenar por:</label>
      <select id="sortOption" name="sortOption">
        <option value="name">Nome</option>
        <option value="state">State</option>
      </select>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { onMounted, defineEmits } from "vue";

let selectedItem: HTMLSelectElement;

onMounted(() => {
  selectedItem = document.getElementById("sortOption") as HTMLSelectElement;
});

const emit = defineEmits(["sortValue"]);

const sendSortValue = () => {
  console.log(selectedItem?.value);
  emit("sortValue", selectedItem?.value);
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.filter-bar {
  font-family: "Roboto", sans-serif;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 53rem;
  height: 3.75rem;
  border: 1px solid #e5e5e5;
  border-radius: 0.25rem;
  padding: 0 0.5rem;
}

.sort-section select {
  border: none;
  outline: none;
  font-size: 0.7rem;
}
.sort-section label {
  font-size: 0.8rem;
}

@media only screen and (max-width: 576px) {
  .filter-bar {
    width: 100%;
    margin-bottom: 0.5rem;
  }

  .items-number {
    font-size: 0.8rem;
  }
}

@media only screen and (min-width: 576px) and (max-width: 768px) {
  .filter-bar {
    width: 100%;
    margin-bottom: 0.5rem;
  }

  .items-number {
    font-size: 0.8rem;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .filter-bar {
    width: 100%;
    margin-bottom: 0.5rem;
  }

  .items-number {
    font-size: 0.8rem;
  }
}

@media only screen and (min-width: 993px) and (max-width: 1200px) {
  .filter-bar {
    width: 100%;
    margin-bottom: 0.5rem;
  }

  .items-number {
    font-size: 0.8rem;
  }
}
</style>
