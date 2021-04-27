<template>
  <div class="task-input">
    <input
      type="text"
      placeholder="New task?"
      :value="task"
      @change="task = $event.target.value"
    />
    <button class="add-task" @click="onCreateTask" />
  </div>
</template>

<script>
export default {
  name: 'TaskInput',

  data: () => ({
    task: ''
  }),

  methods: {
    onCreateTask() {
      if (!this.task) return
      this.$emit('add', this.task)
      this.task = ''
    }
  }
}
</script>

<style scoped>
@import 'style.css';
</style>
