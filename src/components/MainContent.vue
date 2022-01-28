<template>
  <div
    class="main-content px-1 py-5 p-xl-5 p-lg-5 p-md-5 p-sm-5"
    ref="main-content"
    id="main-content"
    v-on:scroll.passive="handleScroll"
  >
    <slot></slot>
    <div
      class="scroll-up"
      :class="{
        hidden: isHidden,
        'slide-up-scroll': toAnimate,
        'slide-down-scroll': !toAnimate,
      }"
      @click="scrollToTop"
    >
      <i class="fas fa-chevron-up fa-2x"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainContent",
  data() {
    return {
      isHidden: true,
      toAnimate: false,
    };
  },
  methods: {
    handleScroll() {
      if (this.$refs["main-content"].scrollTop > 100) {
        this.isHidden = false;
        this.toAnimate = true;
      } else {
        this.toAnimate = false;
      }
    },
    scrollToTop() {
      this.$refs["main-content"].scrollTop = 0;
    },
  },
};
</script>

