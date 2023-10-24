<template>
  <div class="column">
    <div class="is-flex is-align-items-center is-justify-content-space-between">
      <StopWatch :time-to-seconds="timeToSeconds" />

      <button class="button" @click="iniciarTarefa" :disabled="timerIsActive">
        <span class="icon">
          <i class="fas fa-play"></i>
        </span>
        <span>play</span>
      </button>

      <button class="button" @click="finalizarTarefa" :disabled="!timerIsActive">
        <span class="icon">
          <i class="fas fa-stop"></i>
        </span>
        <span>stop</span>
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import StopWatch from './StopWatch.vue'

export default {
  name: 'TimerToForm',
  emits: ['timerFinished'],
  components: {
    StopWatch
  },
  data() {
    return {
      timeToSeconds: 0,
      stopwatch: 0,
      timerIsActive: false
    }
  },

  methods: {
    iniciarTarefa() {
      this.timerIsActive = true
      this.stopwatch = setInterval(() => {
        this.timeToSeconds++
      }, 1000)
    },
    finalizarTarefa() {
      this.timerIsActive = false
      this.$emit('timerFinished', this.timeToSeconds)
      clearInterval(this.stopwatch)
      this.timeToSeconds = 0
    }
  }
}
</script>
