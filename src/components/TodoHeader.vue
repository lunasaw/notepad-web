<template>
  <div>
    <!-- 输入框 -->
    <header class="header">
      <h1>小黑记事本</h1>
      <input placeholder="请输入任务" class="new-todo" @keyup.enter="handleAdd" v-model="todoItem" />
      <button class="add" @click="handleAdd">添加任务</button>
    </header>
  </div>
</template>

<script>
export default {
  data () {
    return {
      todoItem: '',
      doto: {
        name: '',
        isCompleted: false
      }
    }
  },
  methods: {
    handleAdd () {
      if (this.todoItem.trim() === '') {
        return
      }
      this.$emit('add', this.todoItem)
      this.todoItem = ''
    }
  }
}
</script>

<style>
</style>