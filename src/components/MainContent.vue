<template>
  <div class="main-content">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "MainContent",
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
  padding: 0 70px 70px;
  overflow-y: scroll;
  animation: slide-left 0.5s forwards;
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