<template>
  <div class="uls">
    <ul>
      <Myitem
        v-for="item in todos"
        :key="item.uuid"
        :todos="item"
        :checkTodo="checkTodo"
        :deleteTodo="deleteTodo"
      >
      </Myitem>
    </ul>
  </div>
</template>

<script>
import Myitem from "./Myitem.vue";
export default {
  name: "MyList",
  props: ["todos", "checkTodo", "deleteTodo"],
  components: {
    Myitem,
  },
  methods: {},
};
</script>
<style>
.uls ul {
  list-style: none;
  padding: 10px 10px;
}
</style>
