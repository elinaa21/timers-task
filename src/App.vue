<template>
  <div  class="app">
    <div class="container">
      <Timer
        v-for="timer of timers"
        v-bind:timer="timer"
        :key="timer.id"
      />
      <div class="add-timer" @click="addTimer" ref="addTimer">&plus;</div>
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

const timers = [
  { id: 0, hours: 0, minutes: 0, seconds: 0, active: false },
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
      setTimeout(() => this.$refs.addTimer.scrollIntoView(), 0);
    }
  }
}
</script>

<style src="./App.css"></style>
