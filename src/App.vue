<template>
  <div id="app">
    <div class="background">
      <div class="topContainer"></div>
      <TaskComp></TaskComp>
    </div>
  </div>
</template>

<script>
import TaskComp from "./components/TaskComp.vue";

export default {
  name: "App",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
    };
  },
  components: { TaskComp },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100vw;
  margin-left: 0;
  padding: 0px;
}

.background {
  flex-direction: column;
  background-color: #f5f5f5;
  width: 550px;
  height: 100%;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
.topContainer {
  width: 100vw;
  height: 120px;
  background-color: #4caf50;
  border-radius: 5px;
  position: absolute;
  z-index: -99999;
  top: 0;
}
</style>
