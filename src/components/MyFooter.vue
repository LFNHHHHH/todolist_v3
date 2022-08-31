<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" />
    </label>
    <span> <span>已完成{{ checkedNum }}</span> / 全部{{ list.length }} </span>
    <button @click="clearChecked" class="btn btn-danger">清除已完成任务</button>
  </div>
</template>

<script>
import { ref, computed, inject } from 'vue'

export default {
  name: "MyFooter",
  props: ['list'],
  setup (props) {
    let list = inject('list')
    let checkedNum = ref(0)

    checkedNum = computed(() => {
      return props.list.filter(item => item.checked).length
    })

    function clearChecked () { // 清楚已完成
      list = list.filter(item => !item.checked)
      console.log(list)
    }

    return { checkedNum, clearChecked }
  }
};
</script>

<style scoped>
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}
.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}
.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}
.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>