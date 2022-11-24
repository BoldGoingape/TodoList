<template>
  <div class="head">
    <input type="text" placeholder="请输入指定任务" @keyup.enter="addVuale" />
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  name: "MyHead",
  props: ["addStre"],
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addVuale(e) {
      //包装成对象
      if (!e.target.value.trim()) return alert("输入不能为空");
      const todoObj = {
        uuid: nanoid(),
        title: e.target.value,
        dpme: false,
      };
      this.addStre(todoObj);
      e.target.value = "";
    },
  },
};
</script>

<style>
.head input {
  width: 290px;
  height: 30px;
  padding: 5px;
}
</style>
