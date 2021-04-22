<template>
  <MainContent>
    <h1 class="title px-3">A little bit about me</h1>
    <div class="container p-5 mt-3">
      <p class="text-p fs-5">
        <img src="../assets/temp.jpeg" alt="profile-pic" class="profile" />
        I’m a graduate of Electronics Engineering and I’ve taken an interest in
        developing websites. I started studying front-end web development last
        year. However, I had to put my studying on hold when I started my first
        job. At that time, I have already learned the basics of HTML, CSS and
        Javasccript and did few small projects to test what I have learned so
        far.
      </p>
      <br />
      <p class="text-p fs-5">
        I’ve resumed studying web development this year and I’m currently
        learning the basics of back-end development in Udemy. I aim to study web
        development continously and I’m excited to get the point where I can
        create much more interesting and fun projects as I made progress on
        learning it.
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
            class="mt-2 fw-bold badge-white"
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
        "javascript.svg",
        "sass.svg",
        "jquery.svg",
        "bootstrap.svg",
        "vue.png",
        "git.png",
      ],
      tooltip: [false, false, false, false, false, false, false, false],
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
  watch: {
    windowWidth() {
      console.log(this.windowWidth);
    },
  },
};
</script>

<style>
.title {
  font-family: "Anonymous Pro", monospace;
  color: #4ecca3;
  font-size: 50px;
  text-align: left;
  margin-top: 50px;
  opacity: 0;
  animation: fade-in 0.5s 0.7s forwards;
}

.container {
  width: 100% !important;
  max-width: 100% !important;
  text-align: left;
  border-left: 1px solid #4ecca3;
  background: #2d3137;
  color: #eeeeee;
  opacity: 0;
  animation: fade-in 0.5s 0.7s forwards;
}

.profile {
  object-fit: cover;
  width: 150px;
  height: 150px;
  clip-path: circle(50%);
  float: left;
  margin-right: 10px;
}

.text-p {
  font-size: 1.6rem;
  font-weight: 300;
}

.logo {
  position: relative;
  margin-top: 20px;
}

.tooltip_c {
  visibility: hidden;
  position: fixed;
  text-align: center;
  top: 0;
  left: 50%;
  margin-left: -60px;
  background: rgba(78, 204, 163, 0.8);
  font-weight: bold;
  color: #232931;
  padding: 10px;
  width: 100px;
  z-index: 100;
}

.visible {
  visibility: visible;
}

.container div:nth-child(2) {
  justify-content: space-evenly;
}

.w-500 {
  width: 500px;
}

.logo-name {
  font-size: 13px;
}
</style>