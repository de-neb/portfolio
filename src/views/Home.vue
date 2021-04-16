<template>
  <div class="left-bg">
    <h1 class="left-title">Hi I'm</h1>
  </div>
  <div class="right-bg">
    <h1 class="right-title">Eden</h1>
    <h2 class="sub-title">A novice in web designing</h2>
    <Navigation class="nav" />
  </div>
</template>

<script>
import Navigation from "../components/Navigation";

export default {
  name: "Home",
  components: { Navigation },
};
</script>

<style>
.left-bg {
  width: 20vw;
  height: 100vh;
  background: #f9f9f9;
  position: absolute;
  left: 0;
  top: 0;
}

.right-bg {
  width: 80vw;
  height: 100vh;
  background: #bad7df;
  position: absolute;
  right: 0;
  top: 0;
}

.nav {
  top: 50%;
  margin-left: 30px;
}

.left-title {
  font-size: 96px;
  font-family: "Advent Pro", sans-serif;
  position: absolute;
  top: 30%;
  right: 20px;
  font-weight: 500;
}

.right-title {
  font-size: 96px;
  font-family: "Advent Pro", sans-serif;
  position: absolute;
  top: 30%;
  left: 1%;
  font-weight: 500;
}

h2 {
  position: inherit;
  top: 42%;
  left: 1%;
  padding-left: 10px;
}
</style>
