<template>
  <div class="timer">
    <div 
      class="timer__time"
      v-bind:class="{timer__time_active: timer.active}"
    >{{timer.hours ? `${timer.hours}:${timer.minutes}:${timer.seconds}` :
      timer.minutes ? `${timer.minutes}:${timer.seconds}` :
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
    }
  },
  data() {
    return {
      intervalIDs: {}
    }
  }
}
</script>

<style>
.timer {
  width: 225px;
  height: 120px;
  background-color: #696969;
  margin: 0 25px 50px 25px;
}
.timer__time {
  font-size: 22px;
  line-height: 21px;
  color: #9E9E9E;
  font-family: Gotham Pro;
  height: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: #9E9E9E 1px solid;
  box-sizing: border-box;
}
.timer__time_active {
  color: #ffffff;
  border-bottom: #fff 1px solid;
}
.options {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 50%;
}
.play {
  width: 20px;
  height: 20px;
  border: solid;
  border-width: 10px 0px 10px 18px;
  box-sizing: border-box;
  border-color: transparent transparent transparent #9E9E9E;
  cursor: pointer;
  margin-right: 48px;
}
.stop {
  width: 20px;
  height: 20px;
  background-color: #9E9E9E;
  cursor: pointer;
}
.stop_active {
  background-color: white;
}
.pause {
  cursor: pointer;
  width: 20px;
  height: 20px;
  border-style: double;
  border-width: 0px 0px 0px 10px;
  border-color: #ffffff;
  margin-right: 39px;
}
</style>
