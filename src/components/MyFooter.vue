<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" :checked="checkedNum == list.length" @click="checkALL" />
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
    checkedNum = computed(() => { // 计算已完成数量
      return props.list.filter(item => item.checked).length
    })

    function clearChecked () { // 清除已完成
      let newList = JSON.parse(JSON.stringify(list))
      list.length = 0

      newList.forEach(item => {
        if (item.checked == true) return
        list.push(item)
      })
    }

    function checkALL (e) { // 全选全不选
      if (e.target.checked) {
        list.forEach(item => {item.checked = true})
      } else {
        list.forEach(item => {item.checked = false})
      }
    }

    return { checkedNum, clearChecked, checkALL }
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