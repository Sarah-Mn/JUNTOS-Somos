<template>
  <div class="header">
    <img src="../assets/logo.svg" alt="logo-pic" class="logo-img" />
    <SearchBar @searchedValue="emitValue" />
    <div class="skeleton"></div>
    <div class="skeleton"></div>
  </div>
</template>

<script lang="ts" setup>
import { defineEmits } from "vue";
import SearchBar from "./SearchBar.vue";

const emit = defineEmits(["emitValue"]);

const emitValue = (inputValue: string) => {
  emit("emitValue", inputValue);
};
</script>

<style scoped>
.header {
  width: 100%;
  height: 100px;
  background-color: #eee;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

.logo-img {
  width: 9.25rem;
  height: 2.5rem;
  margin: 1.75rem 8.75rem 1.75rem 9.5rem;
}

.skeleton {
  width: 11rem;
  height: 1rem;
  background-color: #d8d8d8;
  border-radius: 1rem;
  margin: 1rem;
}

@media only screen and (max-width: 576px) {
  .header {
    display: block;
  }

  .skeleton {
    display: none;
  }
  .logo-img {
    width: 9.25rem;
    height: 2.5rem;
    margin: 0.5rem 0.5rem;
  }
}

@media only screen and (min-width: 576px) and (max-width: 768px) {
  .header {
    display: flex;
    padding: 0.5rem;
  }

  .skeleton {
    display: none;
  }
  .logo-img {
    width: 9.25rem;
    height: 2.5rem;
    margin: 0.5rem 0.5rem;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .header {
    display: flex;
    padding: 0.5rem;
  }

  /* .skeleton {
    display: none;
  } */
  .logo-img {
    width: 9.25rem;
    height: 2.5rem;
    margin: 0.5rem 0.5rem;
  }
}
</style>
