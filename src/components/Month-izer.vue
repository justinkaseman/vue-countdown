<template>
  <div>
    <div v-if="currentMonth === 11">
      <Snowfall />
      <Tree v-if="currentDay > 15" />
    </div>
  </div>
</template>

<script>
import Snowfall from "./Snowfall.vue";
import Tree from "./Tree.vue";

export default {
  name: "Month-izer",
  components: {
    Snowfall,
    Tree
  },
  computed: {
    currentMonth() {
      return new Date().getMonth();
    },
    currentDay() {
      return new Date().getDate();
    }
  }
};
</script>
<style>
#monthizer-container {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
}
</style>
