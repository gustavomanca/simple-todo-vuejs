<template>
  <section class="progress-bar">
    <h1 class="title">Tasks</h1>
    <div class="bar-wrapper">
      <span class="value"> {{ percentage }}% </span>
      <span class="status" :style="{ width: `${percentage}%` }" />
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProgressBar',

  props: {
    percentage: { type: Number, required: true, default: 0 }
  }
}
</script>

<style scoped>
@import 'style.css';
</style>
