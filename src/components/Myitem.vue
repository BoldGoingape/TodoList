<template>
  <li>
    <input
      type="checkbox"
      :checked="todos.dpme"
      @change="handCheck(todos.uuid)"
    />
    <span v-show="!todos.isEdit">{{ todos.title }}</span>
    <input
      class="int"
      v-show="todos.isEdit"
      type="text"
      :value="todos.title"
      @blur="handleBluer(todos, $event)"
      ref="inputTitle"
    />
    <button @click="deletItem(todos.uuid)">已完成</button>
    <button @click="handLeEdit(todos)" class="btn-eit" v-show="!todos.isEdit">
      编辑
    </button>
  </li>
</template>

<script>
export default {
  name: "MyItme",
  props: ["todos", "checkTodo", "deleteTodo"],
  components: {},
  methods: {
    handCheck(id) {
      this.checkTodo(id);
    },
    //删除
    deletItem(id) {
      if (confirm("确定要删除嘛？")) this.deleteTodo(id);
      // console.log(this.deleteTodo);
    },
    //编辑
    handLeEdit(todos) {
      if ("isEdit" in todos) {
        todos.isEdit = true;
      } else {
        this.$set(todos, "isEdit", true);
      }
      // setTimeout(() => {
      //   this.$refs.inputTitle.focus();
      // }, 100);
      //
      this.$nextTick(function () {
        this.$refs.inputTitle.focus();
      });
    },
    //失去焦点回调
    handleBluer(todos, e) {
      todos.isEdit = false;
      if (!e.target.value.trim()) {
        alert("内容不能为空");
        return;
      }

      this.$bus.$emit("updateTodo", todos.uuid, e.target.value);
    },
  },
  watch: {
    // todos(a, b) {
    //   console.log(a, b);
    // },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.int {
  width: 80px;
}
li {
  padding: 6px;
  margin: 10px;
  border: 1px solid #ccc;
}
li button {
  float: right;
}
.btn-eit {
  margin-right: 10px;
  border: 0px;
}
</style>
