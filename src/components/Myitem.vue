<template>
  <li>
    <input
      type="checkbox"
      :checked="todos.start"
      @change="handCheck(todos.uuid)"
    />
    <span>{{ todos.title }}</span>
    <button @click="deletItem(todos.uuid)">已完成</button>
  </li>
</template>

<script>
export default {
  name: "MyItme",
  props: ["todos", "checkTodo", "deleteTodo"],
  components: {},
  methods: {
    handCheck(id) {
      console.log(id);
      this.checkTodo(id);
    },
    deletItem(id) {
      if (confirm("确定要删除嘛？")) this.deleteTodo(id);
      // console.log(this.deleteTodo);
    },
  },
  watch: {
    todos(a, b) {
      console.log(a, b);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  padding: 6px;
  margin: 10px;
  border: 1px solid #ccc;
}
li button {
  float: right;
}
</style>
