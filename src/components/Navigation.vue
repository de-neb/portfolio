<template>
  <div id="nav">
    <router-link
      class="w-100 text-start"
      v-for="link in navLinks"
      :key="link"
      :to="getLink(link)"
      >{{ link }}<span></span
    ></router-link>
  </div>
</template>

<script>
export default {
  name: "Navigation",
  data() {
    return {
      navLinks: ["Home", "About", "Projects", "Contact"],
    };
  },
  methods: {
    getLink(link) {
      return link === "Home" ? "/" : "/" + link.toLowerCase();
    },
  },
};
</script>


