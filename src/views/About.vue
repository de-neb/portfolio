<template>
  <MainContent>
    <h1 class="title px-3">A little bit about me</h1>
    <div class="container p-5 mt-3">
      <p class="text-p fs-5 light-theme-text">
        <img src="../assets/temp.jpeg" alt="profile-pic" class="profile" />
        I'm graduate of Electronics Engineering and I'm aspiring to become a
        Fullstack Web Developer.
      </p>
      <br />
      <p class="text-p fs-5 light-theme-text">
        I’m excited to get the point where I can create much more interesting
        and fun projects as I've made more progress in my learning.
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

