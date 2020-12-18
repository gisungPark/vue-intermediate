<template>
  <div>
    <todo-header></todo-header>
    <!-- <todo-input v-on:하위 컴포넌트에서 발생시킨 이벤트명="현재 컴포넌트의 메서드 명"></todo-input> -->
    <todo-input v-on:addTodoItem="addOneItem"></todo-input>
    <!-- <todo-list v-bind:"내려보낼 프롭스 속성 이름"="현재위치의 컴포넌트 데이터 속성"></todo-list> -->
    <todo-list v-bind:propsdata="todoItems"></todo-list>
    <todo-footer></todo-footer>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  data: function () {
    return {
      todoItems: [],
    };
  },
  methods: {
    addOneItem: function (todoItem) {
      var obj = { completed: false, item: todoItem };
      // 저장하는 로직
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
  },
  created: function () {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
          this.todoItems.push(
            JSON.parse(localStorage.getItem(localStorage.key(i)))
          );
          // this.todoItems.push(localStorage.key(i));
        }
      }
    }
  },
  components: {
    //컴포넌트 태그명: 컴포넌트 내용
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
    TodoFooter: TodoFooter,
  },
};
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f6;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
