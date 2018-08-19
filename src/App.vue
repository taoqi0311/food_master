<template>
  <div id="app">
    <todo-header :add="add"></todo-header>
    <TodoList :todos="todos" :deleteItem="deleteItem"></TodoList>
    <Spilter></Spilter>
    <todo-footer :todos="todos" :deleteCompleteTodos="deleteCompleteTodos"
                 :selectAllTodos="selectAllTodos"></todo-footer>

  </div>
</template>

<script>
  import TodoList from './components/TodoList'
  import TodoHeader from './components/TodoHeader'
  import TodoFooter from './components/TodoFooter'


  export default {
    name: 'App',
    data() {
      return {
        todos: []
      }
    },
    methods: {
      add(obj) {
        this.todos.unshift(obj)
      },
      deleteItem(index) {
        this.todos.splice(index, 1)
      },
      deleteCompleteTodos() {
        this.todos = this.todos.filter((val) => {
          return !val.complete;
        })
      },
      //选中或取消全选
      selectAllTodos(flag) {
        this.todos.forEach(val => val.complete = flag)
      }
    },
    components: {
      TodoHeader,
      TodoList,
      TodoFooter
    },
    created() {
      window.title = 'food-master'
      this.todos = JSON.parse(localStorage.getItem('food_master') || '[]')
    },
    watch: {
      todos: {
        deep: true,
        handler(val) {
          window.localStorage.setItem('food_master', JSON.stringify(val))
        }
      }
    }
  }
</script>

<style>
  input[type='checkbox'] {
    cursor: pointer;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    border: 1px solid black;
    width: 50%;
    margin: 60px auto;
    box-sizing: border-box;
    height: 500px;
    text-align: center;
  }
</style>
