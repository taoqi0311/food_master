<template>
  <div class="todoFooter">
    <input  type="checkbox" v-model="isAllChecked">
    <span>已完成{{checkedItem}}/全部{{this.todos.length}}</span>
    <i href="#" @click="clearChecked" class="clearChecked">删除选中的任务</i>
  </div>
</template>

<script>
  export default {
    name: "TodoFooter",
    data() {
      return {}
    },
    computed: {
      isAllChecked: {
        get() {
          return this.todos.length > 0 && this.todos.length === this.checkedItem
        },
        set(flag) {
          this.selectAllTodos(flag)
        }

      },
      checkedItem() {
        let count = 0;
        this.todos.forEach(val => {
          if (val.complete)
            count++
        })
        return count
      }

    }
    ,
    props: {
      todos: Array,
      deleteCompleteTodos: Function,
      selectAllTodos: Function
    },
    methods:{
      clearChecked(){
        this.deleteCompleteTodos()
      }
    }
  }
</script>

<style scoped>
  .todoFooter {
    width: 80%;
    margin-left: 10%;
    margin-top: 20px;
    height: 30px;
    line-height: 30px;
    text-align: left;
    font-size: 12px;
  }

  .clearChecked {
    background: red;
    width: 100px;
    text-align: center;
    border-radius: 15px;
    font-size: 12px;
    color: white;
    height: 30px;
    display: inline-block;
    cursor: pointer;
    float: right;
  }
</style>
