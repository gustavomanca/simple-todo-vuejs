<template>
  <section class="tasks-grid">
    <card
      v-for="({ title, status }, index) in tasks"
      :key="index"
      :task="{ index, status, title }"
      @delete="$emit('delete', $event)"
      @status-change="$emit('status-change', { status: $event, index })"
    />
  </section>
</template>

<script>
import Card from '../TaskCard'

export default {
  name: 'TaskGrid',

  props: {
    tasks: { type: Array, required: false, default: () => [] }
  },

  components: {
    Card
  }
}
</script>

<style>
.tasks-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1.6rem;
}
</style>
