<template>
  <div
    class="side-nav d-flex justify-content-center align-items-start flex-column ms-4"
  >
    <h1 class="nav-title text-wrap text-start">Hi I'm Eden</h1>
    <h2 class="sub-text mt-2 text-start" id="subtext">
      aspiring to become a Web Developer
    </h2>
    <Navigation class="nav mt-4" />
    <Illustration class="w-100 illus-bg" />
  </div>
</template>

<script>
import Navigation from "./Navigation";
import Illustration from "./Illustration";
export default {
  name: "SideNav",
  components: { Navigation, Illustration },
};
</script>

<style scoped>
.illus-bg {
  opacity: 0;
  position: absolute;
  bottom: 25%;
  z-index: -1;
  animation: fade-in 1s 0.5s ease-in forwards;
}

@keyframes fade-in {
  to {
    opacity: 0.6;
  }
}
</style>
  
