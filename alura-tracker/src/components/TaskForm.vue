<template>
  <BoxMain>
    <div class="columns">
      <div class="column is-7">{{ task.description }}</div>

      <div class="column">
        <StopWatch v-bind:timeToSeconds="task.timeUsed" />
      </div>
    </div>
  </BoxMain>
</template>

<script lang="ts">
import { type PropType } from 'vue'
import ITasks from '../interfaces/ITask'
import StopWatch from './StopWatch.vue'
import BoxMain from './BoxMain.vue'

export default {
  name: 'TaskForm',
  components: {
    StopWatch,
    BoxMain
  },
  props: {
    task: {
      type: Object as PropType<ITasks>,
      required: true
    }
  }
}
</script>
