<template>
  <MainContent>
    <!-- projects -->
    <h1 class="title text-start mt-5">Projetcs</h1>
    <div class="container p-3 p-md-2 p-sm-1 mt-3 d-flex justify-content-center">
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
                  !project.herokuUrl
                    ? 'https://de-neb.github.io/' + project.url
                    : project.herokuUrl
                "
                v-if="project.title != 'Portfolio v2'"
                type="button"
                class="btn btn-outline-teal light-theme-text"
                target="_blank"
              >
                Live View <i class="fa fa-globe" aria-hidden="true"></i>
              </a>

              <a
                :href="'https://github.com/de-neb/' + project.url"
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
    <h1 class="title">CSS Challenges</h1>
    <p class="text-start mt-3 fs-5 fw-light fade-in light-theme-text">
      I did these challenges to practice and discover some techniques in CSS.
      Some challenges are interactive, while others are animations.
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
              :src="`https://codepen.io/de-neb/embed/${pen.url}?theme-id=light&default-tab=result`"
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
import { projects, pens } from "../ProjectData.js";
export default {
  components: {
    MainContent,
  },
  data() {
    return {
      projects: projects,
      pens: pens,
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