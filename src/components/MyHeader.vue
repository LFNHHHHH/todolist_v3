<template>
  <div class="todo-header">
    <div>{{ test }}</div>
    <div>{{ params.val }}</div>
    <div>{{ params.name }}</div>
    <div>{{ params.age }}</div>
    <input type="text" placeholder="请输入你的任务名称，按回车键确认" />
  </div>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  name: "MyHeader",
  setup () {
    let test = ref('ref...')
    let params = reactive({
      val: 'hello',
      name: 'zs',
      age: 18
    })

    return {test, params}
  }
};
</script>

<style scoped>
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}
.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>