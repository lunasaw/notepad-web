<template>
  <div> <!-- 列表区域 -->
    <section class="main">
      <ul class="todo-list">
        <li class="todo" v-for="(item, index) in todoList" :key="item.id">
          <div class="view">
            <span class="index">{{ index + 1 }}.</span><label>{{item.name}}</label>
            <button class="destroy" @click="handleDel(item.id)"></button>
          </div>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    todoList: Array
  },
  methods: {
    handleDel (id) {
      this.$emit('dell', id)
    }
  }
}
</script>

<style>
</style>