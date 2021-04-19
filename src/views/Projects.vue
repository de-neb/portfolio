<template>
  <MainContent>
    <h1 class="title">Challenges from 100 Days CSS Challenges</h1>
    <p class="text-start mt-3 fs-5 fw-light fade-in">
      I did this challenge in order to pratice and discover some techniques in
      CSS. From the title itself there are 100 challenges where I needed to
      create an exact replica of the challenge for the day. So far I've made 15
      entries and some of these are interactive when clicked or hovered while
      some are pure animation.
    </p>
    <div class="container p-5 d-flex justify-content-center mb-5">
      <div
        id="project-carousel"
        class="carousel slide carousel-dark carousel-fade w-75"
        data-bs-ride="carousel"
      >
        <div class="carousel-indicators">
          <button
            data-bs-target="#project-carousel"
            v-for="(el, i) in pens"
            :key="i"
            :data-bs-slide-to="i"
            class="btn-teal"
            :class="{ active: i == 0 }"
          ></button>
        </div>
        <div class="carousel-inner" role="listbox">
          <div
            class="carousel-item text-center"
            v-for="(pen, index) in pens"
            :class="{ active: index == 0 }"
            :key="pen"
          >
            <iframe
              scrolling="no"
              :title="pen.title"
              :src="
                'https://codepen.io/denksy/embed/' +
                pen.url +
                '?height=500&theme-id=24311&default-tab=result'
              "
              frameborder="no"
              loading="lazy"
              allowtransparency="true"
              allowfullscreen="false"
            >
            </iframe>
          </div>
        </div>

        <button
          type="button"
          class="carousel-control-prev"
          data-bs-target="#project-carousel"
          role="button"
          data-bs-slide="prev"
        >
          <i class="fas fa-chevron-left text-teal fa-3x"></i>
        </button>
        <button
          type="button"
          class="carousel-control-next"
          data-bs-target="#project-carousel"
          role="button"
          data-bs-slide="next"
        >
          <i class="fas fa-chevron-right text-teal fa-3x"></i>
        </button>
      </div>
    </div>
    <h1 class="title text-end mt-5">Projetcs I made so far</h1>
    <div class="container p-5 mt-3 d-flex justify-content-center">
      <div class="row mt-5 justify-content-evenly gap-1">
        <div
          class="card bg-teal mb-5 col-xxl-5 col-xl-5 col-lg-4 col-md-9 col-sm-9 col-9"
          v-for="project in projects"
          :key="project.url"
        >
          <img
            :src="getImg(project.url)"
            class="card-img-top mt-3"
            :alt="project.title"
          />
          <div class="card-body">
            <h5 class="card-title text-teal fw-bold">{{ project.title }}</h5>
            <p class="card-text">
              {{ project.text }}
            </p>
            <div class="row row-cols-auto justify-content-center gap-2">
              <a
                :href="'https://denksy.github.io/' + project.url"
                type="button"
                class="btn btn-outline-teal"
                target="_blank"
              >
                Live View <i class="fa fa-globe" aria-hidden="true"></i>
              </a>

              <a
                :href="'https://github.com/denksy/' + project.url"
                type="button"
                class="btn btn-outline-teal"
                target="_blank"
              >
                Source <i class="fab fa-github" aria-hidden="true"></i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </MainContent>
</template>

<script>
import MainContent from "../components/MainContent";
export default {
  components: {
    MainContent,
  },
  data() {
    return {
      projects: [
        {
          title: "Google Landing Page",
          url: "google-homepage",
          text:
            "I recreated Google's home page using HTML and CSS. No Javascript functionalities were added.",
        },
        {
          title: "Tindog",
          url: "Tindog",
          text:
            "Created a landing page for an imaginary app, Tindog usingHTML and Bootstrap.",
        },
        {
          title: "Python Documentation",
          url: "python-documentation",
          text:
            "This is one of Freecodecamp's required project from Responsive Web Design Projects using HTML and CSS.",
        },
        {
          title: "Youtube (embedding video and images)",
          url: "youtube-homepage",
          text:
            "Recreated Youtube's video content page where I used grid and flex displays. I also made it responsive.",
        },
        {
          title: "Survey Form",
          url: "Survey-Form",
          text:
            "A simple survey form. This is created to pratice creating forms and using diffrent inputs.",
        },
        {
          title: "Simon Game",
          url: "Simon",
          text:
            "This is my very first game with an actual graphics. I used jQuery on this one.",
        },
        {
          title: "Roll the Dice",
          url: "roll-dice",
          text:
            "Created this project to practice Document Object Model manipulation using vanilla Javascript.",
        },
        {
          title: "To-do List",
          url: "To-do-list",
          text:
            "My first web app with CRUD functionality. The To-do lists and items are saved locally in the browser and I also added a Notes section. I made this using Vue.js.",
        },
      ],
      pens: [
        { title: "#63", url: "BaQQLON" },
        { title: "#7", url: "WNoZyQK" },
        { title: "#1", url: "rNWmNxZ" },
        { title: "#2", url: "QWGvVvJ" },
        { title: "#3", url: "qBqjVeW" },
        { title: "#4", url: "XWNgoev" },
        { title: "#5", url: "rNWzzzR" },
        { title: "#6-Notification", url: "mdOBdya" },
        { title: "#8-Raining", url: "vYyWgpV" },
        { title: "#9", url: "eYByZRX" },
        { title: "#12", url: "BaQxdQq" },
        { title: "#13- Bike &amp; Ship", url: "LYbrzqM" },
        { title: "#14- Upload", url: "QWGBXav" },
        { title: "#15 - Shapes", url: "rNWZPaN" },
        { title: "#16", url: "yLVGoPo" },
      ],
    };
  },
  methods: {
    getImg(img) {
      return require(`../assets/${img}.png`);
    },
  },
};
</script>

<style>
iframe {
  width: 410px;
  height: 500px;
}

.card:hover {
  transform: scale(1.03);
  transition: transform 0.5s ease;
}
</style>