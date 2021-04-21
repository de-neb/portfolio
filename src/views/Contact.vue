<template>
  <MainContent>
    <div class="container pb-5 center">
      <h1 class="title mt-0">Get in Touch <span class="dots">...</span></h1>
      <h2>Feel free to send me an email at</h2>
      <i class="far fa-paper-plane mx-1 fs-3"></i>
      <a class="fs-2 email" href="mailto:edenbaui@outlook.com"
        ><i class="fas fa-envelope fa-2x"></i
      ></a>

      <div class="mt-4">
        <h3>You can also find me on</h3>
        <a href="https://github.com/denksy" class="email me-3"
          ><i class="fab fa-github fa-2x"></i
        ></a>

        <a href="https://codepen.io/denksy" class="email"
          ><i class="fab fa-codepen fa-2x"></i
        ></a>
      </div>
    </div>
  </MainContent>
</template>

<script>
import MainContent from "../components/MainContent";
export default {
  name: "Contact",
  components: { MainContent },
};
</script>

<style scoped>
.center {
  margin-top: 160px;
}
</style>
