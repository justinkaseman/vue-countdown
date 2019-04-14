<template>
  <div>
    <Dino
      v-for="i in dinos"
      v-bind:key="i"
      v-bind:i="i"
      v-bind:fancy="fancy"
      v-bind:style="[{ position: 'fixed', bottom: Math.floor(Math.random() * (400 - 0 + 1)) + 0 + 'px' }]"
    />
  </div>
</template>

<script>
import Dino from "./Dino.vue";

export default {
  name: "Dino-izer",
  components: {
    Dino
  },
  props: {
    days: Number,
    hours: Number,
    minutes: Number,
    seconds: Number
  },
  computed: {
    dinos({ days }) {
      const number = 15 - days;
      return number > 0 ? Math.round(number / 2) : 1;
    },
    fancy({ days }) {
      return days === 0;
    }
  }
};
</script>
<style>
#dinoizer-container {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
}
</style>
