<template>
  <div class="footer">
    <div class="logo"><Logo /></div>
    <div class="text">juntos somos mais fidelizacao S.A.</div>
    <div class="social">
      Siga-nos nas redes sociais:
      <div class="icons">
        <div class="facebook"><i class="fab fa-facebook-f fb"></i></div>
        <div class="linkedin"><i class="fab fa-linkedin-in ldn"></i></div>
        <div class="instagram"><i class="fab fa-instagram insg"></i></div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import Logo from "./Logo.vue";
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.icons {
  display: flex;
  justify-content: center;
  align-items: center;
}

.facebook,
.linkedin,
.instagram {
  width: 2.5rem;
  height: 2.5rem;
  border-radius: 50%;
  background-color: #28b0fc;
  margin: 1rem 0.5rem;
}
.fb,
.ldn,
.insg {
  text-align: center;
  font-size: 1.5rem;
  margin-top: 6px;
  margin-left: 1px;
}
.footer {
  width: 100%;
  height: 18.5rem;
  background-color: #3a3a3a;
  padding-top: 2rem;
  /* margin: 0 auto; */
}

.logo {
  width: 10.2rem;
  margin: 2rem auto 0;
}

.text {
  font-family: "Roboto", sans-serif;
  color: #ffffff;
  font-weight: 500;
  font-size: 1rem;
  text-align: center;
  margin-top: 1.5rem;
  text-transform: capitalize;
}

.social {
  font-family: "Roboto", sans-serif;
  color: #ffffff;
  font-weight: 400;
  font-size: 0.9rem;
  text-align: center;
  margin-top: 1.5rem;
}
</style>
