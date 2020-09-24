<template>
  <div  class="app">
    <div class="container">
      <Timer
        v-for="timer of timers"
        v-bind:timer="timer"
        :key="timer.id"
      />
      <div class="add-timer" @click="addTimer">&plus;</div>
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

const timers = [
  { id: 0, hours: 0, minutes: 0, seconds: 0, active: true },
  { id: 1, hours: 0, minutes: 0, seconds: 0, active: false },
  { id: 2, hours: 0, minutes: 0, seconds: 0, active: false },
];

export default {
  name: 'App',
  components: {
    Timer
  },
  data() {
    return {
      timers
    }
  },
  methods: {
    addTimer() {
      const newTimer = {
        id: Date.now + Math.floor(Math.random() * 9999),
        hours: 0,
        minutes: 0,
        seconds: 0,
        active: false
      };
      this.timers.push(newTimer);
    }
  }
}
</script>

<style>
@media (max-width: 1300px) {
  .container {
    width: 80% !important;
  }
}
@media (max-width: 1031px) {
  .container {
    width: 85% !important;
  }
}
@media (max-width: 1024px) {
  .container {
    width: 60% !important;
  }
}
@media (max-width: 917px) {
  .container {
    width: 65% !important;
  }
}
@media (max-width: 847px) {
  .container {
    width: 75% !important;
  }
}
@media (max-width: 768px) {
  .container {
    width: 50% !important;
    justify-content: center !important;
  }
}
@media (max-width: 531px) {
  .container {
    width: 99% !important;
    justify-content: center !important;
  }
}
.app {
  background-color: #353638;
  overflow: scroll;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  margin: 0 auto;
  width: 60%;
  height: max-content;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
}

.add-timer {
  width: 225px;
  height: 120px;
  background-color: #696969;
  font-size: 35px;
  text-align: center;
  color: #9E9E9E;
  margin-bottom: 7%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 25px 50px 25px;
}
.add-timer:hover {
  color: white;
  cursor: pointer;
}
</style>
