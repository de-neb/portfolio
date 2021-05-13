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
  <div class="switch-position">
    <div class="switch-body">
      <input
        type="checkbox"
        name=""
        id="checkbox"
        v-model="switchOn"
        @click="switchTheme"
      />
      <div class="switch">
        <i
          class="fas fa-2x"
          :class="{ 'fa-moon': !switchOn, 'fa-sun': switchOn }"
        ></i>
      </div>
    </div>
  </div>
  <SideNav
    v-if="$route.name !== 'Home'"
    :class="{ 'show-side-nav': menuActive }"
    id="side-nav"
    ref="side-nav"
    @clicked="closeMenu"
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
      switchOn: false,
    };
  },
  methods: {
    closeMenu() {
      setTimeout(() => {
        this.menuActive = false;
      }, 100);
    },
  },
  computed: {
    switchTheme() {
      let app = document.getElementById("app");
      if (!this.switchOn) {
        app.classList.add("dark-theme");
        app.classList.remove("light-theme");
      } else {
        app.classList.remove("dark-theme");
        app.classList.add("light-theme");
      }
    },
  },
  updated() {
    let setTheme = { theme: this.switchOn };
    localStorage.setItem("theme", JSON.stringify(setTheme));
  },
  mounted() {
    if (localStorage.getItem("theme")) {
      const { theme } = JSON.parse(localStorage.getItem("theme"));
      this.switchOn = theme;
    }
    //set theme, switchTheme func can't be called in mounted
    let app = document.getElementById("app");
    if (!this.switchOn) {
      app.classList.add("light-theme");
    } else {
      app.classList.remove("light-theme");
    }
  },
};
</script>

<style scoped>
.send-backwards {
  z-index: -1;
}
</style>