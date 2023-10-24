<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logo da Alura" />
    </h1>
  </header>
</template>

<script lang="ts">
export default { name: 'LateralBar' }
</script>

<style scoped>
header {
  background-color: #0d3b66;
  width: 90%;
  height: 100vh;
  padding: 2.5rem;
}
@media only screen and (max-width: 768px) {
  header {
    height: auto;
  }
}
</style>
