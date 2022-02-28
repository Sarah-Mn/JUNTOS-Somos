<template>
  <div class="card">
    <img :src="people?.picture.medium" alt="profile-pic" class="profile-pic" />
    <div class="name">{{ people?.name.first }} {{ people?.name.last }}</div>
    <div class="street">{{ streetName }}, {{ streetNumber }}</div>
    <div class="city">{{ people?.location.city }}</div>
    <div class="postcode">
      {{ people?.location.state }} - CEP: {{ people?.location.postcode }}
    </div>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, ref } from "vue";
const props = defineProps({
  people: Object,
});

const street = ref(props.people?.location.street);
const parsedStreet = street.value.split(" ");
const streetNumber = parsedStreet[0];
const streetName = parsedStreet.slice(1, parsedStreet.length - 1).join("  ");
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.card {
  width: 17rem;
  height: 19.5rem;
  margin: 0.5rem 1rem 1rem 0rem;
  border: 1px solid #e5e5e5;
  border-radius: 0.25rem;
}

.profile-pic {
  width: 6rem;
  height: 6rem;
  border-radius: 50%;
  margin: 2.1rem 5.5rem 0.75rem 5.5rem;
}

.name {
  width: 15rem;
  font-family: "Roboto", sans-serif;
  text-transform: capitalize;
  font-weight: 900;
  font-size: 1.25rem;
  margin: 0 auto;
  text-align: center;
}

.street {
  width: 15rem;
  font-family: "Roboto", sans-serif;
  text-transform: capitalize;
  font-weight: 900;
  font-size: 0.8rem;
  margin: 1rem auto;
  text-align: center;
}

.city {
  width: 15rem;
  font-family: "Roboto", sans-serif;
  text-transform: capitalize;
  font-weight: 900;
  font-size: 0.75rem;
  margin: 1rem auto 0;
  text-align: center;
}

.postcode {
  width: 15rem;
  font-family: "Roboto", sans-serif;
  text-transform: capitalize;
  font-weight: 900;
  font-size: 0.75rem;
  margin: 0 auto;
  text-align: center;
}

@media only screen and (max-width: 576px) {
  .card {
    width: 17.7rem;
    height: 19.5rem;
    margin: 0;
    margin-bottom: 0.5rem;
  }
}
</style>
