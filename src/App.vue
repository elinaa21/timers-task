<template>
  <div  class="app">
    <div class="container">
      <Timer
        v-for="timer of timers"
        v-bind:timer="timer"
        :key="timer.id"
      />
      <div class='add-timer'>&plus;</div>
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
  }
}
</script>

<style>
.app {
  background-color: #353638;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.container {
  margin: 0 auto;
  width: 55%;
  height: max-content;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.add-timer {
  width: 225px;
  height: 120px;
  background-color: #696969;
  font-size: 25px;
  text-align: center;
  color: #9E9E9E;
  margin-bottom: 7%;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
