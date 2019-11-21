<template>
  <div>
    <Snowf
      :amount="50"
      :size="5"
      :speed="1.5"
      :wind="0"
      :opacity="0.8"
      :swing="1"
      :image="null"
      :zIndex="null"
      :resize="true"
      color="#fff"
    />
  </div>
</template>

<script>
import Snowf from "vue-snowf";
export default {
  name: "Snowfall",
  components: {
    Snowf
  }
};
</script>

<style>
#snowfall-container {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
}
</style>
