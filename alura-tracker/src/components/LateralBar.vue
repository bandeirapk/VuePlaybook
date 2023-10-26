<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logo da Alura" />
    </h1>

    <button class="button" @click="switchTheme">
      <span>
        <i
          class="fa-solid"
          :class="{ 'fa-moon': isDarkModeActive, 'fa-sun': !isDarkModeActive }"
        ></i>
        {{ textButton }}
      </span>
    </button>
  </header>
</template>

<script lang="ts">
export default {
  name: 'LateralBar',
  emits: ['switchTheme'],
  data() {
    return {
      isDarkModeActive: false
    }
  },
  computed: {
    textButton() {
      if (this.isDarkModeActive) {
        return 'Light Mode'
      }
      return 'Dark Mode'
    }
  },
  methods: {
    switchTheme() {
      this.isDarkModeActive = !this.isDarkModeActive
      console.log('O valor na lateral bar => ', this.isDarkModeActive)
      this.$emit('switchTheme', this.isDarkModeActive)
    }
  }
}
</script>

<style scoped>
header {
  background-color: #0d3b66;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    height: auto;
  }
}
</style>
