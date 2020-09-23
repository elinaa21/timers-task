<template>
  <div class="timer">
    <div 
      class="timer__time"
      v-bind:class="{timer__time_active: timer.active}"
    >{{timer.hours}}:{{timer.minutes}}:{{timer.seconds}}</div>
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
  }
}
</script>

<style>
.timer {
  width: 225px;
  height: 120px;
  background-color: #696969;
  margin-bottom: 7%;
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
}
</style>
