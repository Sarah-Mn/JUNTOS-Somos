<template>
  <div class="path-container">
    <div class="path">Home > Usuarios > Detalhes</div>

    <div class="title">Lista de membros</div>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.path-container {
  padding: 1.5rem 9.75rem;
}

.path {
  font-family: "Roboto", sans-serif;
  font-size: 0.8rem;
  font-weight: 700;
}

.title {
  font-family: "Roboto", sans-serif;
  font-size: 2rem;
  font-weight: bold;
}
@media only screen and (max-width: 576px) {
  .path-container {
    padding: 4rem 1rem 0;
  }
}

@media only screen and (min-width: 576px) and (max-width: 768px) {
  .path-container {
    padding: 1rem 1rem 0;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .path-container {
    padding: 1rem 1rem 0;
  }
}
</style>
