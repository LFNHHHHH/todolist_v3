<template>
  <div class="todo-header">
    <input type="text" v-model="params.val" @keydown.enter="add" placeholder="请输入你的任务名称，按回车键确认" />
  </div>
</template>

<script>
import { reactive } from 'vue'
export default {
  name: "MyHeader",
  setup (props, context) {
    let params = reactive({
      val: '',
    })

    function add () {
      // 获取数据，把数据给APP组件
      context.emit('add', params.val)
      params.val = ''
    }

    return {params, add}
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