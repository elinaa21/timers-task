<template>
  <div class="timer">
    <div 
      class="timer__time"
      v-bind:class="{timer__time_active: timer.active}"
    >{{timer.hours ? `${timer.hours}:${add0(timer.minutes)}:${add0(timer.seconds)}` :
      timer.minutes ? `${timer.minutes}:${add0(timer.seconds)}` :
      `${timer.seconds}` 
    }}</div>
    <div class="options">
      <div 
        class="play" 
        v-if="!timer.active" 
        @click="playTimer"
      ></div>
      <div class="pause" v-else @click="pauseTimer"></div>
      <div 
        class="stop"
        v-bind:class="{stop_active: timer.active}"
        @click="stopTimer"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  props: {
    timer: {
      type: Object,
      required: true
    }
  },
  methods: {
    playTimer() {
      this.timer.active = !this.timer.active;
      this.intervalIDs[this.timer.id] = setInterval(() => {
        if (this.timer.seconds === 59 && this.timer.minutes === 59) {
          this.timer.hours++;
          this.timer.minutes = 0;
          this.timer.seconds = 0;
        } else if (this.timer.seconds === 59) {
          this.timer.minutes++;
          this.timer.seconds = 0;
        } else {
          this.timer.seconds++;
        }
      }, 1000);
    },
    pauseTimer() {
      this.timer.active = !this.timer.active;
      clearInterval(this.intervalIDs[this.timer.id]);
      delete this.intervalIDs[this.timer.id];
    },
    stopTimer() {
      if (this.timer.active) {
        this.timer.active = !this.timer.active;
      }
      if (this.intervalIDs[this.timer.id]) {
        clearInterval(this.intervalIDs[this.timer.id]);
        delete this.intervalIDs[this.timer.id];
      }
      this.timer.seconds = 0;
      this.timer.minutes = 0;
      this.timer.hours = 0;
    },
    add0(number) {
      return number < 10 ? '0' + number : number;
    }
  },
  data() {
    return {
      intervalIDs: {}
    }
  }
}
</script>

<style src="./Timer.css"></style>
