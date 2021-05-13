<template>
  <div class="side-nav ms-xl-2 ms-lg-2 ms-md-0 px-sm-1 px-1">
    <h1 class="nav-title text-wrap text-center">Hi I'm Eden</h1>
    <h2 class="sub-text mt-2 text-center" id="subtext">
      aspiring to become a Web Developer
    </h2>
    <Navigation class="nav mt-4" @link-clicked="sendToApp" />
    <Illustration class="w-100 illus-bg" />
  </div>
</template>

<script>
import Navigation from "./Navigation";
import Illustration from "./Illustration";
export default {
  name: "SideNav",
  components: { Navigation, Illustration },
  methods: {
    sendToApp() {
      this.$emit("clicked");
    },
  },
};
</script>

<style scoped>
.illus-bg {
  opacity: 0;
  position: absolute;
  top: 50%;
  z-index: -1;
  animation: fade-in 1s 0.5s ease-in forwards;
}

.side-nav {
  min-height: -webkit-fill-available !important;
}

@media (max-width: 450px) {
  .side-nav {
    width: 100% !important;
  }
}

@keyframes fade-in {
  to {
    opacity: 0.9;
  }
}
</style>
  
