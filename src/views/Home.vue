<template>
  <div>
    <Header @emitValue="getValue" />
    <Path />
    <Main :searching="searchValue" />
    <Footer />
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import Header from "../components/Header.vue";
import Path from "../components/Path.vue";
import Main from "../components/Main.vue";
import Footer from "../components/Footer.vue";

const searchValue = ref("");

const getValue = (b: string) => {
  searchValue.value = b;
  // console.log("home: ", searchValue.value);
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  /* width: 100%; */
  /* background-color: red; */
}
</style>
