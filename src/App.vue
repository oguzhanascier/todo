<template>
  <div class="container d-flex justify-content-center align-items-center">
    <div class="todo-container shadow bg-dark">
      <new-task
        @exportItem="todoListItem.push($event)"
        :setText="input.text"

      ></new-task>
      <todo-list :todos="todoListItem" @data="input.text= $event"></todo-list>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import NewTask from "./components/NewTask.vue";
export default {
  components: {
    TodoList,
    NewTask,
  },
  data() {
    return {
      input: {
        text:null,
        isEdit: true,

      },
      todoListItem: [
        { id: 110, text: "Yangın İhbar", isCompleted: true },
        { id: 36, text: "Activex El Temizleme Jeli", isCompleted: false },
       
        
      ],
    };
  },
  methods: {
    getIndex() {},
  },
};
</script>

<style>
body {
  min-width: 100vw;
  background-color: #212529;
}
.container {
  min-height: 100vh;
}

.todo-container {
  padding: 50px;
  width: 450px;
  min-height: 600px;
  border-radius: 20px;
  filter: drop-shadow(1px 1px 1px rgba(255, 255, 255, 0.707));
}
</style>
