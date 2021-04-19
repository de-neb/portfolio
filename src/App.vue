<template>
  <SideNav />
  <div class="hr"></div>
  <router-view />
</template>

<script>
import SideNav from "./components/SideNav";
export default {
  name: "App",
  components: { SideNav },
};
</script>


<style>
</style>
