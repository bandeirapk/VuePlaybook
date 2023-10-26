<template>
  <div class="box form">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="description"
        />
      </div>
      <TimerToForm @timerFinished="finalizarTarefa" />
    </div>
  </div>
</template>

<script lang="ts">
import TimerToForm from './TimerToForm.vue'

export default {
  name: 'UserForm',
  components: {
    TimerToForm
  },
  emits: ['saveTask'],
  data() {
    return {
      description: ''
    }
  },
  methods: {
    finalizarTarefa(timeUsed: number): void {
      if (this.description === '') {
        alert('Você precisa informar uma descrição para a tarefa!')
      } else {
        this.$emit('saveTask', {
          description: this.description,
          timeUsed
        })
        this.description = ''
      }
    }
  }
}
</script>

<style>
.form {
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
</style>
