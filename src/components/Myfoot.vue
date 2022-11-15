<template>
  <div>
    <input type="checkbox" @change="checkAll" />
    <span>已完成{{ AllSelect }}</span
    >/
    <span>总任务{{ tatal }}</span>
    <button @click="DelSel">删除所选</button>
  </div>
</template>

<script>
export default {
  name: "MyFoot",
  props: ["tatal", "AllSelect", "checkAllTodo", "DeletSelectTod"],
  components: {},
  computed: {
    isAll() {
      return this.doneToto === this.total && this.total < 0;
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
