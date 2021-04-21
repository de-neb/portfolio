<template>
  <SideNav v-if="$route.name !== 'Home'" />
  <!-- <div class="hr" v-if="$route.name != 'Home'"></div> -->
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
