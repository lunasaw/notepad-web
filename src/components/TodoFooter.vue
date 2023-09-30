<template>
  <div>

    <!-- 统计和清空 -->
    <footer class="footer">
      <!-- 统计 -->
      <span class="todo-count">合 计:<strong> {{this.todoList.length}} </strong></span>
      <!-- 清空 -->
      <button class="clear-completed" @click="handleDellAll">
        清空任务
      </button>
    </footer>
  </div>
</template>

<script>
export default {
  props: {
    todoList: Array
  },
  methods: {
    handleDellAll () {
      this.$emit('dellAll')
    }
  }
}
</script>

<style>
</style>