<template>
  <div
    class="side-nav d-flex justify-content-center align-items-start flex-column ms-4"
  >
    <h1 class="nav-title caret" id="greet"></h1>
    <h1 class="nav-title caret mt-3" id="name"></h1>
    <h2 class="sub-text mt-2 text-start" id="subtext">
      Aspiring to be a web developer
    </h2>
    <Navigation class="nav mt-5" />
  </div>
</template>

<script>
import Navigation from "./Navigation";
export default {
  name: "SideNav",
  components: { Navigation },
  data() {
    return {
      greet: "Hi I'm",
      name: "Eden.",
    };
  },
  methods: {
    typewriter(id, text) {
      for (let i in text) {
        setTimeout(() => {
          document.getElementById(id).innerHTML += text.charAt(i);
        }, i * 200);
      }
    },
    animateTitle() {
      this.typewriter("greet", this.greet);
      setTimeout(() => {
        document.getElementById("greet").classList.remove("caret");
        this.typewriter("name", this.name);
      }, this.greet.length * 200);
    },
  },
  mounted() {
    this.animateTitle();
  },
};
</script>
  
