<template>
  <div>
    <div class="todo" v-for="(todo, index) in todos" :key="index">
      <div class="taskList">
        <i
          class="fa-solid fa-check text-white"
          @click="completed(todo)"
          :class="{ checked: todo.isCompleted }"
        ></i>
        <ul class="list-group border-none">
          <li
            class="list-group-item bg-dark text-light"
            :class="{ textChecked: todo.isCompleted }"
          >
            {{ todo.text }} 
          </li>
        </ul>
      </div>
      <i class="fa-solid fa-trash-can" @click="deleteTodo(index)"></i>
    </div>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  props: ["todos"],

  methods: {
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    completed(todo) {
      todo.isCompleted = !todo.isCompleted;
    },
  },

};
</script>

<style scoped>
.todo {
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid rgba(255, 255, 255, 0.19);
  padding: 5px 0;
}

.list-group-item {
  border: none;
}

.taskList {
  display: flex;
  align-items: center;
 
}

i {
  cursor: pointer;
}

.fa-trash-can {
  color: #ff9292;
  opacity: 0;
}

.todo:hover .fa-trash-can {
  cursor: pointer;
  opacity: 1;
  transition: all .5s ease-in-out;
}

.checked {
  color: lightgreen !important;
  transition: all .5s ease-in-out;
}
.textChecked {
  text-decoration: line-through;
  color: #968d8d44 !important;
  transition: all .5s ease-in;
}
</style>
