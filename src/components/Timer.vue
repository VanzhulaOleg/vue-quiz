<template>
  <section class="timer" id="timer">
    <time class="timer__main">
      <img class="logo-vue" alt="Vue logo" src="../assets/logo.png" />
      <span id="minutes">{{ minutes }}</span>
      <span id="middle">:</span>
      <span id="seconds">{{ seconds }}</span>
    </time>
    <footer class="timer__text" v-if="finishText">время окончания</footer>
  </section>
</template>
<script>
export default {
  name: "timer",
  props: ["timerEvent"],
  data: function () {
    return {
      finishText: false,
      timer: null,
      totalTime: 0,
    };
  },
  mounted() {
    this.timer = setInterval(() => this.countdown(), 1000);
    // if (this.timerEvent) {
    // this.eventsTimer();
    // }
  },
  watch: {
    timerEvent: function () {
      // watch it
      this.eventsTimer();
    },
  },
  methods: {
    eventsTimer: function () {
      if (this.timerEvent === "stop") {
        clearInterval(this.timer);
        this.timer = null;
        this.finishText = true;
        console.log(this.finishText);
      } else {
        this.timer = null;
        this.finishText = false;
        this.totalTime = 0;
        this.timer = setInterval(() => this.countdown(), 1000);
      }
    },
    padTime: function (time) {
      return (time < 10 ? "0" : "") + time;
    },
    countdown: function () {
      if (this.totalTime >= 0) {
        this.totalTime++;
      } else {
        this.totalTime = 0;
        this.resetTimer;
      }
    },
  },

  computed: {
    minutes: function () {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds: function () {
      const seconds = this.totalTime - this.minutes * 60;
      return this.padTime(seconds);
    },
  },
};
</script>
<style >
.timer {
  position: absolute;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  top: 10vh;
  left: 10vh;
  color: #000000;
  font-size: 30px;
}
.logo-vue {
  height: 8vh;
  width: 8vh;
}
.timer__main {
  display: flex;
  justify-content: center;
  align-items: center;
}
.timer__text {
  font: 0.6em sans-serif;
}
@media (max-width: 768px) {
  .timer {
    top: 5vh;
    left: 4vh;
    z-index: 4;
  }
  .logo-vue {
    height: 6vh;
    width: 6vh;
  }
  .timer__main {
    font: 0.5em sans-serif;
  }
  .timer__text {
    font: 0.5em sans-serif;
  }
}
</style>
