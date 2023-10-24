<script lang="ts">
import LateralBar from './components/LateralBar.vue'
import FormUser from './components/UserForm.vue'
import TaskForm from './components/TaskForm.vue'
import ITasks from './interfaces/ITask'
import BoxMain from './components/BoxMain.vue'

export default {
  name: 'App',
  components: {
    LateralBar,
    FormUser,
    TaskForm,
    BoxMain
  },
  data() {
    return {
      tasks: [] as ITasks[]
    }
  },
  computed: {
    verifyListEmpty(): boolean {
      return this.tasks.length === 0
    }
  },
  methods: {
    addTask(task: ITasks): void {
      this.tasks.push(task)
    }
  }
}
</script>

<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <LateralBar />
    </div>

    <div class="column is-three-quarter">
      <FormUser @saveTask="addTask" />
      <div class="list">
        <TaskForm v-for="(task, index) in tasks" v-bind:key="index" v-bind:task="task" />
        <BoxMain v-if="verifyListEmpty"> Você não está produtivo hoje :/ </BoxMain>
      </div>
    </div>
  </main>
</template>

<style>
.list {
  padding: 1.25rem;
}
</style>
