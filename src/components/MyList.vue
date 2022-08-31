<template>
  <ul class="todo-main">
    <template v-for="item in list" :key="item.id">
      <MyItem :item="item" />
    </template>
  </ul>
</template>

<script>
import MyItem from "./MyItem";
export default {
  name: "MyList",
  components: { MyItem },
  props: ['list'],
};
</script>

<style scoped>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}
.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>