<template>
  <MainContent>
    <!-- projects -->
    <h1 class="title text-start mt-5">Projetcs</h1>
    <div class="container p-5 p-md-2 p-sm-1 mt-3 d-flex justify-content-center">
      <div class="row mt-5 justify-content-evenly gap-2">
        <div
          class="
            card
            bg-teal
            mb-5
            col-xxl-4 col-xl-5 col-lg-7 col-md-7 col-sm-9 col-12
          "
          v-for="(project, i) in projects"
          :key="project.url"
          :class="{ 'col-md-6': i === projects.length - 1 }"
        >
          <img
            :src="getImg(project.url)"
            class="card-img-top mt-3"
            :alt="project.title"
          />
          <div class="card-body">
            <h5 class="card-title text-teal fw-bold">{{ project.title }}</h5>
            <p class="card-text light-theme-text">
              {{ project.text }}
            </p>
            <span
              class="badge badge-white mb-3 px-3 mx-1 fs-6"
              v-for="tool in project.tools"
              :key="tool"
              >{{ tool }}</span
            >
            <div class="row row-cols-auto justify-content-center gap-2">
              <a
                :href="
                  !project.heroku
                    ? 'https://denksy.github.io/' + project.url
                    : project.herokuUrl
                "
                type="button"
                class="btn btn-outline-teal light-theme-text"
                target="_blank"
              >
                Live View <i class="fa fa-globe" aria-hidden="true"></i>
              </a>

              <a
                :href="'https://github.com/denksy/' + project.url"
                type="button"
                class="btn btn-outline-teal light-theme-text"
                target="_blank"
              >
                Source <i class="fab fa-github" aria-hidden="true"></i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- css challenge -->
    <h1 class="title">Challenges from 100 Days CSS Challenges</h1>
    <p class="text-start mt-3 fs-5 fw-light fade-in light-theme-text">
      I did this challenge in order to practice and discover some techniques in
      CSS. From the title itself there are 100 challenges where I needed to
      create an exact replica of the challenge for the day. So far I've made 15
      entries and some of these are interactive when clicked or hovered while
      some are pure animation.
    </p>
    <div
      class="
        container
        m-0
        p-xl-5 p-lg-5 p-md-3
        py-sm-3
        px-sm-0
        d-flex
        justify-content-center
        mb-5
      "
    >
      <div
        id="project-carousel"
        class="carousel slide carousel-dark carousel-fade w-75"
        data-bs-ride="carousel"
      >
        <div class="carousel-indicators mx-0">
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
              :src="`https://codepen.io/denksy/embed/${pen.url}?theme-id=light&default-tab=result`"
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
          title: "Simon Game",
          url: "Simon",
          text: "This is my first game with an actual graphics. I used jQuery on this one.",
          tools: ["HTML", "CSS", "Javascript", "jQuery"],
        },
        {
          title: "Roll the Dice",
          url: "roll-dice",
          text: "Created this project to practice Document Object Model manipulation using vanilla Javascript.",
          tools: ["HTML", "CSS", "Javascript"],
        },
        {
          title: "Reaction Timer",
          url: "reaction-timer",
          text: "My first project using Vue and it's CLI. It measures how quickly you can click the block.",
          tools: ["HTML", "CSS", "Vue"],
        },
        {
          title: "To-do List",
          url: "To-do-list",
          text: "My first web app with CRUD functionality. You can create a 'task list' and add 'to-do' items inside. You can also set a 'to-do' item's priority, date and details. Each task list and its items are saved locally in the browser, so it can be accessed again when visiting the page. I also added a notes section.",
          tools: ["HTML", "CSS", "Javascript", "Vue", "Sass"],
        },
        {
          title: "Newsletter Sign Up",
          url: "newsletter-signup",
          text: "This is created after learning some of the basics in Node.js and using an API particularly Mailchimp's Marketing API.",
          tools: ["HTML", "CSS", "Javascript", "Bootstrap", "Node.js"],
          heroku: true,
          herokuUrl: "https://owl-newsletter-signup.herokuapp.com/",
        },
        {
          title: "Portfolio v2",
          url: "web-portfolio-v2",
          text: "I decided to improved my first portfolio using Vue and after learning the set up for Vue's routes. I think using Vue made my code more readable and organized compared on my first portfolio where I just used pure HTML, CSS and Javascript. Although, I also think that the same could still be achieved if I didn't use any framework like Vue it's just that I'll be seeing probably a lot of HTML elements in my Javascript file. In this version I only used three colors for my color scheme and went for a very simple design. I also added a light and dark theme.",
          tools: ["HTML", "CSS", "Sass", "Bootstrap", "Vue"],
        },
        {
          title: "Weather for Today",
          url: "weather-project",
          text: "This web app uses OpenWeatherMap API for getting the weather data and Geolocation API for detecting the user's location. I also used Node.js for handling requests in the server and deployed the web app in Heroku. You can search the weather updates of any location or allow the app to pinpoint your location (though low accuracy for now). I wanted to try creating backgrounds for this project so I made a night and day backgrounds using Figma. The style is heavily influenced by Kurzgesagt art style.",
          tools: [
            "HTML",
            "CSS",
            "Javascript",
            "Bootstrap",
            "Sass",
            "Node.js",
            "EJS",
          ],
          heroku: true,
          herokuUrl: "https://weather-4-today.herokuapp.com/",
        },
        {
          title: "Movie Library",
          url: "movie-library",
          text: "In this website you can browse upcomming, popular or top rated movies. You can also search for a movie and see it's information, or look for movies with specific genres. I used the TheMovieDatabase's API for the data. I also used Nuxt (a Vue framework) for this project which made creating components, pages and routing easier.",
          tools: ["HTML", "CSS", "Bootstrap", "Vue", "Nuxt"],
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
        { title: "#18", url: "RwgyOma" },
        { title: "#19", url: "GREGaKZ" },
        { title: "#20", url: "NWgBJRL" },
        { title: "#21", url: "ZEyqYpQ" },
        { title: "22", url: "OJgavwj" },
        { title: "23", url: "vYZQrjM" },
        { title: "24", url: "XWgoajv" },
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