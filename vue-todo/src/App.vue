<template>
  <div id="app"></div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

var my_cmp = {
  template: "<div>my component</div>",
};

export default {
  components: {
    //컴포넌트 태그명: 컴포넌트 내용
    TodoHeader: TodoHeader,
  },
};
</script>

<style>
</style>
