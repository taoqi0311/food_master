<template>
  <li @mouseenter="enter(true)" @mouseleave="enter(false)" @click="changeCheck">
    <label>
      <input type="checkbox" v-model="todo.complete">
      <span>{{todo.title}}</span>
    </label>
    <button class="btn" v-show="isShow" @click="deleteObj">删除</button>
    <Spilter></Spilter>
  </li>
</template>

<script>
  export default {
    name: "TodoItem",
    props: {
      index: Number,
      todo: Object,
      deleteItem: Function
    },
    data() {
      return {
        isShow: false
      }
    },
    methods: {
      deleteObj() {
        let sure = window.confirm(`确定删除${this.todo.title}吗?`)
        if (sure)
          this.deleteItem(this.index)

      },
      enter(flag) {
        this.isShow = flag
      },
      changeCheck(){
        this.todo.complete = !this.todo.complete
      }

    }
  }
</script>

<style scoped>
  li {
    height: 50px;
    line-height: 50px;
  }

  li:hover {
    background: gray;
  }

  .btn {
    float: right;
    background: red;
    color: white;
    width: 40px;
    height: 30px;
    border-radius: 10px;
    margin-top: 10px;
    margin-right: 20px;
    right: 0;
    outline: none;
    vertical-align: middle;
    border: none;
    cursor: pointer;
  }
</style>
