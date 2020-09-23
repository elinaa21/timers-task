<template>
  <div class="timer">
    <div 
      class="timer__time"
      v-bind:class="{timer__time_active: timer.active}"
    >{{timer.hours}}:{{timer.minutes}}:{{timer.seconds}}</div>
    <div class="options">
      <div class="left-img play" v-if="!timer.active"></div>
      <img src="../assets/square.png">
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
  box-sizing: border-box;
}
.options {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 50%;
}
.left-img {
  margin-right: 48px;
}
.play {
  width: 20px;
  height: 20px;
  border: #696969 solid;
  border-width: 10px 0px 10px 18px;
  box-sizing: border-box;
  border-color: transparent transparent transparent #9E9E9E;
}
</style>
