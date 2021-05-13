<template>
  <div id="nav">
    <router-link
      class="w-100 text-start link mb-4 typing"
      v-for="link in navLinks"
      :key="link"
      :to="getLink(link)"
      @click="sendToSideNav"
      >{{ link }}<span></span
    ></router-link>
    <a
      :href="'https://docs.google.com/viewer?url=' + pdfLink"
      class="w-100 text-start link mb-4"
      target="_blank"
      >Resume</a
    >
    <div class="info text-start">
      <a href="https://github.com/denksy" class="email me-3"
        ><i class="fab fa-github fa-1x"></i
      ></a>

      <a href="https://codepen.io/denksy" class="email me-3"
        ><i class="fab fa-codepen fa-1x"></i
      ></a>

      <a class="email" href="mailto:edenbaui@outlook.com"
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
      pdfLink:
        "https://raw.githubusercontent.com/denksy/web-portfolio-v2/65cc881f55c89702f333f9203d90ef043de8e287/resume/resume-eden-baui.pdf",
    };
  },
  methods: {
    getLink(link) {
      return link === "Home" ? "/" : "/" + link.toLowerCase();
    },
    sendToSideNav() {
      this.$emit("link-clicked");
    },
  },
};
</script>
