<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        {{ list }}
        <MyHeader @add="add" />
        <MyList :list="list" />
        <MyFooter :list="list" />
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, provide } from 'vue'
import MyHeader from "./components/MyHeader";
import MyList from "./components/MyList";
import MyFooter from "./components/MyFooter.vue";
export default {
  name: "App",
  components: { MyHeader, MyList, MyFooter },
  setup () {
    let list = reactive([
      {
        id: new Date().getTime() + parseInt(Math.random() * new Date().getTime()),
        checked: true,
        title: '吃饭'
      }, {
        id: new Date().getTime() + parseInt(Math.random() * new Date().getTime()),
        checked: false,
        title: '睡觉'
      }, {
        id: new Date().getTime() + parseInt(Math.random() * new Date().getTime()),
        checked: false,
        title: '打豆豆'
      }
    ])
    provide('list', list)

    function add (val) {
      list.unshift({
        id: new Date().getTime() + parseInt(Math.random() * new Date().getTime()),
        checked: false,
        title: val
      })
    }

    function updataList (val) {
      console.log("updataList======")
      console.log(this.list)
      console.log(val)
      list = val
      console.log(list)
    }
    provide('updataList', updataList)

    console.log(list)

    return { list, add }
  }
};
</script>

<style>
body {
  background: #fff;
}
.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
    0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}
.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}
.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}
.btn:focus {
  outline: none;
}
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>