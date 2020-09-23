<template>
  <div  class="app">
    <Timer />
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

const timers = [
  { id: 0, hours: 0, minutes: 0, seconds: 0, active: false }
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
  justify-content: center;
  align-items: center;
}
</style>
