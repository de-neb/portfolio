<template>
  <MainContent>
    <h1 class="title px-3">A little bit about me</h1>
    <div class="container p-5 mt-3">
      <p class="text-p fs-5 light-theme-text">
        I am a graduate of Electronics Engineering and aspiring to become a
        Fullstack Web Developer. I learned the basics of Javascript sometime in
        2020 and started learning front-end web development last year. As I made
        progress on learning web development, I also wanted to expand my
        knowledge in back-end web development. Learning full stack web
        development is challenging but fun and rewarding at the same time. And I
        look forward to showcasing my skills, improving them, and creating more
        projects.
      </p>
    </div>
    <h1 class="title text-start px-3">Tools I've used so far</h1>
    <div class="container p-1 py-5 d-flex justify-content-center mt-3">
      <div class="row row-cols-1 justify-content-around w-500">
        <div
          class="logo col-3 text-center"
          v-for="(logo, index) in logos"
          :key="logo"
          :class="{ 'mt-4': index > 3 }"
          @mouseover="showTooltip(index)"
          @mouseleave="hideTooltip(index)"
          @mousemove="followCursor($event, logo)"
        >
          <img :src="getLogo(logo)" :alt="logo + '-logo'" class="w-75" />
          <span
            class="mt-2 fw-bold light-theme-text"
            :class="{
              visible: tooltip[index],
              tooltip_c: windowWidth > 975,
              'd-block': windowWidth <= 975,
              'logo-name': windowWidth < 425,
            }"
            :id="logo + '-tooltip'"
            >{{ logo.replace(/.png|.svg/, "").toUpperCase() }}</span
          >
        </div>
      </div>
    </div>
  </MainContent>
</template>

<script>
import MainContent from "../components/MainContent";
export default {
  name: "About",
  components: {
    MainContent,
  },
  data() {
    return {
      logos: [
        "html5.svg",
        "css3.png",
        "sass.svg",
        "bootstrap.svg",
        "javascript.svg",
        "vue.png",
        "nuxt.png",
        "node js.svg",
        "mongoDB.svg",
        "git.png",
      ],
      tooltip: Array(10).fill(false),
      windowWidth: window.innerWidth,
    };
  },
  methods: {
    getLogo(logo) {
      return require("../assets/" + logo);
    },
    showTooltip(index) {
      this.tooltip[index] = true;
    },
    hideTooltip(index) {
      this.tooltip[index] = false;
    },
    followCursor(e, logo) {
      const tooltipId = document.getElementById(logo + "-tooltip");
      tooltipId.style.left = e.pageX + 60 + "px";
      tooltipId.style.top = e.pageY + 10 + "px";
    },
  },
  mounted() {
    window.onresize = () => {
      this.windowWidth = window.innerWidth;
    };
  },
};
</script>

