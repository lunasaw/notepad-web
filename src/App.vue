<template>
  <section id="app">
    <TodoHeader @add="handleAdd"></TodoHeader>
    <TodoMain :todoList="list" @dell="handleDell"></TodoMain>
    <TodoFooter :todoList="list" @dellAll="handleDellAll"></TodoFooter>
  </section>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  },
  data () {
    return {
      list: []
    }
  },
  mounted () {
    let data = JSON.parse(localStorage.getItem("todoList"));
    if (data && data.length > 0) {
      this.list = data;
    } else {
      this.list = [
        { id: 1, name: '吃饭饭', isCompleted: false },
        { id: 2, name: '睡觉觉', isCompleted: false },
        { id: 3, name: '打豆豆', isCompleted: true }
      ]
    }
  },
  watch: {
    list: {
      handler (newVal) {
        window.localStorage.setItem('todoList', JSON.stringify(newVal))
      },
      deep: true
    }
  },
  methods: {
    handleAdd (todoItem) {
      this.list.push({
        id: this.list.length + 1,
        name: todoItem,
        isCompleted: false
      })
    },
    handleDell (id) {
      this.removeItem(id)
    },
    handleDellAll () {
      this.list = []
    },
    removeItem (id) {
      const index = this.list.findIndex(item => item.id === id);
      if (index !== -1) {
        this.list.splice(index, 1);
      }
      // id 重新排序
      this.list.forEach((item, index) => {
        item.id = index + 1;
      })
    }
  }
}
</script>

<style>
</style>
