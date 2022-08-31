<template>
  <li>
    <label>
      <input type="checkbox" :checked="item.checked" @click="check" />
      <span>{{ item.title }}</span>
    </label>
    <button @click="delItem" class="btn btn-danger">删除</button>
  </li>
</template>

<script>
import { inject } from 'vue'

export default {
  name: "MyItem",
  props: ['item'],
  setup (props) {
    let list = inject('list')

    function check () { // 选中事件
      let index = list.findIndex(item => item.id === props.item.id)
      list[index].checked = !list[index].checked
    }

    function delItem () { // 删除
      let index = list.findIndex(item => item.id === props.item.id)
      list.splice(index, 1)
    }
    
    return { check, delItem }
  }
};
</script>

<style scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}
li label {
  float: left;
  cursor: pointer;
}
li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}
li button {
  float: right;
  display: none;
  margin-top: 3px;
}
li:before {
  content: initial;
}
li:last-child {
  border-bottom: none;
}
li:hover {
  background-color: #ddd;
}
li:hover button {
  display: block;
}
</style>