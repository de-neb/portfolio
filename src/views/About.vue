<template>
  <MainContent>
    <h1 class="title">A little bit about me</h1>
    <div class="container p-5 mt-3">
      <p class="text-p">
        <img src="../assets/temp.jpeg" alt="profile-pic" class="profile" />
        I’m a graduate of Electronics Engineering and I’ve taken an interest in
        developing websites. I started studying front-end web development last
        year. However, I had to put my studying on hold when I started my first
        job. At that time, I have already learned the basics of HTML, CSS and
        Javasccript and did few small projects to test what I have learned so
        far.
      </p>
      <br />
      <p class="text-p">
        I’ve resumed studying web development this year and I’m currently
        learning the basics of back-end development in Udemy. I aim to study web
        development continously and I’m excited to get the point where I can
        create much more interesting and fun projects as I made progress on
        learning it.
      </p>
    </div>
    <h1 class="title text-end">Tools I've used so far</h1>
    <div class="container p-5 d-flex justify-content-center mt-3">
      <div class="row row-cols-xl-4 row-cols-xs-2 justify-content-around w-500">
        <div
          class="logo col-3"
          v-for="(logo, index) in logos"
          :key="logo"
          @mouseover="showTooltip(index)"
          @mouseleave="hideTooltip(index)"
          @mousemove="followCursor($event, logo)"
        >
          <img :src="getLogo(logo)" :alt="logo + '-logo'" class="w-100" />
          <span
            class="tooltip_c"
            :class="{ visible: tooltip[index] }"
            :id="logo + '-tooltip'"
            >{{ logo.replace(/.png|.svg/, "").toUpperCase() }}</span
          >
        </div>
      </div>
    </div>
  </MainContent>
  <RightSideNav />
</template>

<script>
import RightSideNav from "../components/RightSideNav";
import MainContent from "../components/MainContent";
export default {
  name: "About",
  components: {
    RightSideNav,
    MainContent,
  },
  data() {
    return {
      logos: [
        "html5.svg",
        "css3.png",
        "javascript.svg",
        "jquery.svg",
        "bootstrap.svg",
        "vue.png",
        "git.png",
      ],
      tooltip: [false, false, false, false, false, false, false],
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
  updated() {},
};
</script>

<style>
.title {
  font-family: "Advent Pro", sans-serif;
  font-size: 50px;
  text-align: left;
  margin-top: 50px;
  opacity: 0;
  animation: fade-in 0.5s 0.7s forwards;
}

.container {
  width: 100%;
  text-align: left;
  background: #bad7df;
  box-shadow: 7px 7px 5px #66777c;
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

.w-500 {
  width: 500px;
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
  background: rgba(73, 73, 73, 0.8);
  font-weight: 400;
  color: #fffdf6;
  padding: 10px;
  width: 100px;
  border-radius: 5px;
  z-index: 100;
}

.visible {
  visibility: visible;
}

.container div:nth-child(2) {
  justify-content: space-evenly;
}
</style>