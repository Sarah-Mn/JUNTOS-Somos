<template>
  <div class="card">
    <div class="image" />
    <div class="name"></div>
    <div class="street"></div>
    <div class="city"></div>
    <div class="postcode"></div>
  </div>
</template>

<style scoped>
.card {
  width: 17rem;
  height: 19.5rem;
  margin: 0.5rem 0.5rem 1rem 0.5rem;
  border: 1px solid #e5e5e5;
  border-radius: 0.25rem;
}
.image {
  background-color: #eee;
  width: 6rem;
  height: 6rem;
  border-radius: 50%;
  margin: 2.1rem 5.5rem 0.75rem 5.5rem;
}

.name {
  height: 16px;
  display: block;
  background-color: #eee;
  width: 15rem;
  margin: 2rem auto;
  text-align: center;
  border-radius: 2rem;
}

.street {
  height: 18px;
  background-color: #eee;
  width: 10rem;
  margin: 1rem auto;
  text-align: center;
  border-radius: 2rem;
}

.city {
  height: 10px;
  background-color: #eee;
  width: 8rem;
  margin: 1rem auto 0;
  text-align: center;
  border-radius: 2rem;
}
</style>
