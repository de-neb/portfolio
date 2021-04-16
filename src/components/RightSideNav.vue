<template>
  <div class="right-side-nav">
    <Navigation class="side-nav" />
  </div>
</template>

<script>
import Navigation from "./Navigation";
export default {
  name: "RightSideNav",
  components: {
    Navigation,
  },
};
</script>
  
<style>
.right-side-nav {
  background: #bad7df;
  width: 20vw;
  height: 100vh;
  position: absolute;
  right: 0;
  animation: slide-right 0.6s forwards;
}

.side-nav {
  left: 30px;
  top: 50px;
  opacity: 0;
  animation: fade-in 0.5s 0.6s forwards;
}

@keyframes slide-right {
  from {
    width: 0;
  }
  to {
    width: 20vw;
  }
}
</style>