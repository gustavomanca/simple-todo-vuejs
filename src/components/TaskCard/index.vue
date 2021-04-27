<template>
  <div
    class="task-card"
    :class="{ '--done': task.status }"
    @click="$emit('status-change', !task.status)"
  >
    <button class="clear-task" @click="$emit('delete', task.index)" />
    <span class="task-title">
      {{ task.title }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'TaskCard',

  props: {
    task: { type: Object, required: true, default: () => {} }
  }
}
</script>

<style scoped>
@import 'style.css';
</style>
