<template>
  <div class="main-content">
    <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style>
.main-content {
  background: #f9f9f9;
  width: 80vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  padding: 0 70px 70px;
  overflow-y: scroll;
  animation: slide-left 0.5s forwards;
}

/* //scrollbar style */
.main-content::-webkit-scrollbar {
  background: #f9f9f9;
}

/* Handle */
.main-content::-webkit-scrollbar-thumb {
  background: #8ab6d6;
}
</style>