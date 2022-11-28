<template>
  <div id="app">
    <MyboxVue
      :todos="todos"
      :addStre="addStre"
      :checkTodo="checkTodo"
      :deleteTodo="deleteTodo"
      :checkAllTodo="checkAllTodo"
      :DeletSelectTod="DeletSelectTod"
    >
      <!-- <MyListVue></MyListVue>
      <MyfootVue></MyfootVue> -->
    </MyboxVue>
  </div>
</template>

<script>
import MyboxVue from "./components/Mybox.vue";
// import MyListVue from "./components/MyList.vue";
// import MyfootVue from "./components/Myfoot.vue";
export default {
  name: "App",
  data() {
    return {
      todos: JSON.parse(localStorage.getItem("todos")) || [],
    };
  },
  components: {
    MyboxVue,
    // MyListVue,
    // MyfootVue,
  },
  methods: {
    addStre(todoObj) {
      this.todos.unshift(todoObj);
    },
    //改
    updateTodo(id, title) {
      this.todos.forEach((todo) => {
        if (todo.uuid == id) todo.title = title;
      });
    },
    //选项
    checkTodo(id) {
      this.todos.forEach((todo) => {
        if (todo.uuid === id) todo.dpme = !todo.dpme;
      });
    },
    //删除
    deleteTodo(dataid) {
      this.todos = this.todos.filter((todo) => {
        return todo.uuid !== dataid;
      });
    },
    //全选或者全不选
    checkAllTodo(dpme) {
      this.todos.forEach((todo) => {
        todo.dpme = dpme;
      });
    },
    //删除所有已完成
    DeletSelectTod() {
      this.todos = this.todos.filter((todo) => {
        return !todo.dpme;
      });
    },
  },
  watch: {
    //监视 深度
    todos: {
      deep: true,
      handler(value) {
        localStorage.setItem("todos", JSON.stringify(value));
      },
    },
  },
  mounted() {
    this.$bus.$on("updateTodo", this.updateTodo);
  },
};
</script>

<style></style>
