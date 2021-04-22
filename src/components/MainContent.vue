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
        hidden: hide,
        'slide-up-scroll': animate,
        'slide-down-scroll': !animate,
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
      hide: true,
      animate: false,
    };
  },
  methods: {
    handleScroll() {
      if (this.$refs["main-content"].scrollTop > 100) {
        this.hide = false;
        this.animate = true;
      } else {
        this.animate = false;
      }
    },
    scrollToTop() {
      this.$refs["main-content"].scrollTop = 0;
    },
  },
};
</script>

