<template>
  <div class="hello">
    <h3>今日任务</h3>
    <MyHeare :addStre="addStre"></MyHeare>
    <myliset :todos="todos"></myliset>
    <MyFoot></MyFoot>
  </div>
</template>

<script>
import MyHeare from "./MyHead.vue";
import MyFoot from "./Myfoot.vue";
import Myliset from "./MyList.vue";
export default {
  name: "MyBox",
  props: ["todos", "addStre"],
  components: {
    MyHeare,
    Myliset,
    MyFoot,
  },
  methods: {
    // eslint-disable-next-line vue/no-dupe-keys
    addStre(todoObj) {
      console.log(this.todo);
      console.log(todoObj);
      //   this.todos.unshift(todoObj);
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  margin: 40px auto;
  width: 300px;
  border: 2px solid #ccc;
  padding: 10px 10px;
}
.hello h3 {
  text-align: center;
}
</style>
