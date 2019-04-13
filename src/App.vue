<template>
  <div id="app">
    <Light/>
  </div>
</template>

<script>
import Countdown from "./components/Countdown.vue";
import Dinoizer from "./components/Dino-izer.vue";
import Light from "./components/Light.vue";
export default {
  name: "app",
  components: {
    Countdown,
    Dinoizer,
    Light
  }
};
</script>

<style>
html,
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  font-style: italic;
  font-size: 4.2vmin;
  line-height: 4.7vmin;
  text-align: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: rgba(255, 255, 255, 0.6);
  margin: 0;
  padding: 0;
  height: 100%;
  background: rgb(184, 90, 144);
  background: -moz-linear-gradient(
    top,
    rgb(184, 90, 144) 0%,
    rgb(54, 30, 42) 73%,
    rgb(24, 13, 19) 100%
  );
  background: -webkit-gradient(
    left top,
    left bottom,
    color-stop(0%, rgb(184, 90, 144)),
    color-stop(73%, rgb(54, 30, 42)),
    color-stop(100%, rgb(24, 13, 19))
  );
  background: -webkit-linear-gradient(
    top,
    rgb(184, 90, 144) 0%,
    rgb(54, 30, 42) 73%,
    rgb(24, 13, 19) 100%
  );
  background: -o-linear-gradient(
    top,
    rgb(184, 90, 144) 0%,
    rgb(54, 30, 42) 73%,
    rgb(24, 13, 19) 100%
  );
  background: -ms-linear-gradient(
    top,
    rgb(184, 90, 144) 0%,
    rgb(54, 30, 42) 73%,
    rgb(24, 13, 19) 100%
  );
  background: linear-gradient(
    to bottom,
    rgb(184, 90, 144) 0%,
    rgb(54, 30, 42) 73%,
    rgb(24, 13, 19) 100%
  );
}
</style>
