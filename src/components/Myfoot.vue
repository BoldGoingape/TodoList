<template>
  <div v-show="total">
    <input type="checkbox" @change="checkAll" :checked="isAll" />
    <span>已完成{{ AllSelect }}</span
    >/
    <span>总任务{{ total }}</span>
    <button @click="DelSel">删除所选</button>
  </div>
</template>

<script>
export default {
  name: "MyFoot",
  props: ["todos", "checkAllTodo", "DeletSelectTod"],

  components: {},
  computed: {
    total() {
      return this.todos.length;
    },
    AllSelect() {
      let i = 0;
      this.todos.forEach((todo) => {
        if (todo.dpme) i++;
      });
      return i;
    },
    isAll() {
      return this.AllSelect === this.total && this.total > 0;
    },
  },
  methods: {
    checkAll(e) {
      this.checkAllTodo(e.target.checked);
    },
    DelSel() {
      if (confirm("确定要删除所有嘛")) this.DeletSelectTod();
    },
  },
};
</script>

<style scoped>
button {
  float: right;
}
</style>
