<template>
  <section>
    <strong>{{ timed }}</strong>
  </section>
</template>

<script lang="ts">
export default {
  name: 'StopWatch',
  props: {
    timeToSeconds: {
      type: Number,
      default: 0
    }
  },
  computed: {
    timed(): string {
      return new Date(this.timeToSeconds * 1000).toISOString().slice(11, 19)
    }
  }
}
</script>
