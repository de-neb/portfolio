<template>
  <div class="menu" v-if="$route.name !== 'Home'">
    <input
      type="checkbox"
      class="burger-check"
      id="menu-notes"
      v-model="menuActive"
    />
    <div class="burger">
      <div class="bar"></div>
      <div class="bar"></div>
      <div class="bar"></div>
    </div>
  </div>
  <SideNav
    v-if="$route.name !== 'Home'"
    :class="{ 'show-side-nav': menuActive }"
    id="side-nav"
    ref="side-nav"
  />
  <router-view />
</template>

<script>
import SideNav from "./components/SideNav";
export default {
  name: "App",
  components: { SideNav },
  data() {
    return {
      menuActive: false,
    };
  },
};
</script>

