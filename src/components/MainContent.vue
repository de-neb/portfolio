<template>
  <div
    class="main-content px-xxl-5 px-3"
    ref="main-content"
    id="main-content"
    v-on:scroll.passive="handleScroll"
  >
    <slot></slot>
    <div :class="{ 'scroll-up': appear }" @click="scrollToTop">
      <i class="fas fa-chevron-up fa-2x"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainContent",
  data() {
    return {
      appear: false,
    };
  },
  methods: {
    handleScroll() {
      if (this.$refs["main-content"].scrollTop > 20) {
        this.appear = true;
      } else {
        this.appear = false;
      }
    },
    scrollToTop() {
      this.$refs["main-content"].scrollTop = 0;
    },
  },
};
</script>

<style>
.main-content {
  background: #232931;
  width: 80vw;
  height: 90vh;
  position: absolute;
  top: 50%;
  right: 0;
  margin-top: -45vh;
  display: flex;
  flex-direction: column;
  overflow-y: scroll;
  border-left: 1px solid #4ecca3;
  animation: slide-left 0.5s forwards;
  scroll-behavior: smooth !important;
}

/* //scrollbar style */
.main-content::-webkit-scrollbar {
  background: #232931;
  width: 3px;
}

/* Handle */
.main-content::-webkit-scrollbar-thumb {
  background: #4ecca3;
}
</style>