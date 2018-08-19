<template>
  <ul>
    <todo-item v-for="(todo,index) in todos" :key="index" :todo="todo" :index="index"
               :deleteItem="deleteItem"></todo-item>
  </ul>
</template>

<script>
  import TodoItem from './TodoItem'

  export default {
    name: "TodoList",
    props: ['todos', 'deleteItem'],
    components: {
      TodoItem
    }
  }
</script>

<style scoped lang="less">
  @base: 80%;
  ul {
    overflow: auto;
    width: @base;
    height: 70%;
    list-style: none;
    padding: 0;
    text-align: left;
    margin-left: 10%;
  }
</style>
