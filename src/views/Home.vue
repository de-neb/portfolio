<template>
  <div class="home text-teal">
    <h1 class="home-title text-center" ref="home-greet">
      <span class="caret" ref="caret0"></span>
    </h1>
    <h2 class="sub-text mt-2 text-start text-center" ref="home-subtext">
      <span class="" ref="caret1"></span>
    </h2>
    <div
      class="
        container-fluid
        d-flex
        align-items-center
        justify-content-center
        position-relative
        gap-0
        mt-5
      "
    >
      <Navigation id="nav" class="fs-2 d-flex flex-column fade-in" />
      <Illustration class="illus inline-block" />
    </div>
  </div>
</template>

<script>
import MainContent from "../components/MainContent";
import Navigation from "../components/Navigation";
import Illustration from "../components/Illustration";
export default {
  name: "Home",
  components: { MainContent, Navigation, Illustration },
  data() {
    return {
      mainText: ["Hi I'm Eden", "aspiring to become a Web Developer"],
    };
  },
  methods: {
    typing(index) {
      this.mainText[index].split("").forEach((letter, i) => {
        setTimeout(() => {
          this.$refs["caret" + index].insertAdjacentHTML("beforebegin", letter);
        }, i * 30);
      });
    },
  },
  mounted() {
    this.typing(0);
    setTimeout(() => {
      this.typing(1);
      this.$refs["caret0"].classList.remove("caret");
      this.$refs["caret1"].classList.add("caret");
    }, this.mainText[0].length * 100 + 300);
    setTimeout(() => {
      this.$refs["caret1"].classList.remove("caret");
    }, 3000);
  },
};
</script>

<style scoped>
.home {
  height: 100vh;
  margin: auto;
  display: flex;
  justify-content: center;
  flex-direction: column;
  width: 90%;
}

.caret {
  background: #4ecca3;
  width: 7px;
  height: 100%;
}

#nav {
  width: 200px;
}

.fade-in {
  animation-delay: 2.8s !important;
}

svg {
  min-width: 350px;
}

@media (max-width: 615px) {
  .home-title {
    font-size: 70px;
  }
}

@media (max-width: 505px) {
  .home-title,
  .nav-title {
    font-size: 60px;
  }
  svg {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, 0);
    z-index: 1;
    opacity: 0.6;
  }
  #nav {
    margin-right: auto;
  }
}

@media (max-width: 480px) {
  .home-title,
  .nav-title {
    font-size: 55px;
  }
}
</style>