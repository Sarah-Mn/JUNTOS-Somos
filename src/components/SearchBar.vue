<template>
  <div class="search-bar">
    <input
      type="search"
      placeholder="Buskar aqui"
      class="search-input"
      v-model="inputValue"
      @input="sendSearchedValue"
    />
    <i class="fas fa-search icon"></i>
  </div>
</template>

<script lang="ts" setup>
import { defineEmits, ref } from "vue";

const inputValue = ref("");

const emit = defineEmits(["searchedValue"]);

const sendSearchedValue = () => {
  emit("searchedValue", inputValue.value);
};
</script>

<style scoped>
.search-bar {
  position: relative;
  width: 80%;
  margin: 0 auto;
}
.search-input {
  width: 100%;
  height: 3rem;
  padding: 0.5rem;
  padding-left: 2.2rem;
  outline: none;
  border: 1px solid #b0b0b0;
  border-radius: 2rem;
}

.icon {
  position: absolute;
  left: 15px;
  top: 50%;
  transform: translateY(-50%);
}
</style>
