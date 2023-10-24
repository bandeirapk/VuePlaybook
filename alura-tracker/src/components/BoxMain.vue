<template>
  <div class="box has-text-weight-bold">
    <slot></slot>
  </div>
</template>

<script lang="ts">
export default {
  name: 'BoxMain'
}
</script>

<style scoped>
.box {
  background-color: #faf0ca;
}
</style>
