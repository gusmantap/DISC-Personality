<template>
  <Disc />
</template>

<script>
import Disc from "./components/Disc.vue";
export default {
  name: "App",
  components: {
    Disc,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}

.w-full {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
}

.btn {
  cursor: pointer;
  color: #fff;
  background: #FFA655;
  padding: 10px 30px;
  border: none;
  border-radius: 30px;
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.3);
}
</style>
