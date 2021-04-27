<template>
  <div id="app">
    <progress-bar :percentage="percentageOfDoneTasks" />
    <task-input @add="onCreateTask" />
    <tasks-grid
      :tasks="tasks"
      @delete="onDeleteTask"
      @status-change="onHandleStatusChange"
    />
  </div>
</template>

<script>
import ProgressBar from '@/components/ProgressBar'
import TaskInput from '@/components/TaskInput'
import TasksGrid from '@/components/TasksGrid'

export default {
  name: 'App',

  components: {
    ProgressBar,
    TaskInput,
    TasksGrid
  },

  data: () => ({
    tasks: []
  }),

  computed: {
    percentageOfDoneTasks() {
      if (!this.tasks.length) return 0

      const total = this.tasks.length
      const doneTasks = this.tasks.filter(({ status }) => status).length
      const percentage = Math.floor((doneTasks / total) * 100)
      return percentage
    }
  },

  methods: {
    onCreateTask(title) {
      this.tasks.push({ title, status: false })
    },

    onDeleteTask(index) {
      this.tasks.splice(index, 1)
    },

    onHandleStatusChange({ index, status }) {
      Object.assign(this.tasks[index], { status })
    }
  }
}
</script>

<style>
@import './global.css';
</style>
