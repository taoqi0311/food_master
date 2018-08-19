<template>
  <div>
    <input class="todoHeader" type="text" v-model="title" @keyup.enter="addItem">
  </div>
</template>

<script>
  export default {
    name: "TodoHeader",
    props: {
      add: Function
    },
    data: function () {
      return {
        title: ''
      }
    },
    methods: {
      addItem() {
        let title = this.title.trim();
        if (!title) {
          alert('请输入内容')
          return
        }
        let obj = {title, complete: false}
        this.add(obj)
        this.title = ''
      }
    },
    watch: {
      title(val, oldval) {
        if (val.length > 15) {
          alert('输入内容长度不能大于15个字!');
          this.title = oldval;
        }
      }
    }
  }
</script>

<style lang="less" scoped>
  @base: 80%;
  .todoHeader {
    width: @base;
    height: 30px;
    margin-top: 10px;
  }
</style>
