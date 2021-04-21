<template>
  <div id="nav">
    <router-link
      class="w-100 text-start link mb-4 typing"
      v-for="link in navLinks"
      :key="link"
      :to="getLink(link)"
      >{{ link }}<span></span
    ></router-link>
    <div class="info text-start">
      <a href="https://github.com/denksy" class="email me-3"
        ><i class="fab fa-github fa-1x"></i
      ></a>

      <a href="https://codepen.io/denksy" class="email me-3"
        ><i class="fab fa-codepen fa-1x"></i
      ></a>

      <a class="fs-2 email" href="mailto:edenbaui@outlook.com"
        ><i class="fas fa-envelope fa-1x"></i
      ></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navigation",
  data() {
    return {
      navLinks: ["Home", "About", "Projects"],
    };
  },
  methods: {
    getLink(link) {
      return link === "Home" ? "/" : "/" + link.toLowerCase();
    },
  },
};
</script>
