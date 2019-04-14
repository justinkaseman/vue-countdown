<template>
  <div v-if="!loading">
    <div id="countdown-container">
      <ul class="vuejs-countdown">
        <li v-if="days > 0">
          <p class="digit">{{ days | twoDigits }}</p>
          <p class="text">{{ days > 1 ? 'days' : 'day' }}</p>
        </li>
        <li>
          <p class="digit">{{ hours | twoDigits }}</p>
          <p class="text">{{ hours > 1 ? 'hours' : 'hour' }}</p>
        </li>
        <li>
          <p class="digit">{{ minutes | twoDigits }}</p>
          <p class="text">min</p>
        </li>
        <li>
          <p class="digit">{{ seconds | twoDigits }}</p>
          <p class="text">Sec</p>
        </li>
      </ul>
    </div>
    <Dinoizer v-bind:days="days"/>
  </div>
</template>

<script>
import Dinoizer from "./Dino-izer.vue";
let interval = null;
export default {
  name: "Countdown",
  components: {
    Dinoizer
  },
  props: {
    end: {
      type: String
    }
  },
  data() {
    return {
      now: Math.trunc(new Date().getTime() / 1000),
      date: null,
      diff: 0,
      loading: true
    };
  },
  created() {
    if (!this.end) {
      throw new Error("Missing props 'end'");
    }
    this.date = Math.trunc(Date.parse(this.end) / 1000);
    if (!this.date) {
      throw new Error("Invalid props value, correct the 'end'");
    }
    interval = setInterval(() => {
      this.now = Math.trunc(new Date().getTime() / 1000);
    }, 1000);
  },
  computed: {
    seconds() {
      return Math.trunc(this.diff) % 60;
    },
    minutes() {
      return Math.trunc(this.diff / 60) % 60;
    },
    hours() {
      return Math.trunc(this.diff / 60 / 60) % 24;
    },
    days() {
      return Math.trunc(this.diff / 60 / 60 / 24);
    }
  },
  watch: {
    now() {
      this.loading = false;
      this.diff = this.date - this.now;
      if (this.diff <= 0 || this.stop) {
        this.diff = 0;
        // Remove interval
        clearInterval(interval);
      }
    }
  },
  filters: {
    twoDigits(value) {
      if (value.toString().length <= 1) {
        return "0" + value.toString();
      }
      return value.toString();
    }
  },
  destroyed() {
    clearInterval(interval);
  }
};
</script>
<style>
#countdown-container {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 30%;
  margin: 0 auto;
}
.vuejs-countdown {
  padding: 0;
  margin: 0;
}
.vuejs-countdown li {
  display: inline-block;
  margin: 0 8px;
  text-align: center;
  position: relative;
}
.vuejs-countdown li p {
  margin: 0;
}
.vuejs-countdown li:after {
  content: ":";
  position: absolute;
  top: 5px;
  right: -13px;
  font-size: 32px;
}
.vuejs-countdown li:first-of-type {
  margin-left: 0;
}
.vuejs-countdown li:last-of-type {
  margin-right: 0;
}
.vuejs-countdown li:last-of-type:after {
  content: "";
}
.vuejs-countdown .digit {
  font-size: 32px;
  font-weight: 600;
  line-height: 1.4;
  margin-bottom: 0;
}
.vuejs-countdown .text {
  text-transform: uppercase;
  margin-bottom: 0;
  font-size: 18px;
}
</style>
