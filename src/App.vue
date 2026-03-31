<template>
  <div id="app" class="container" :class="[mode ? 'dark-mode' : 'light-mode']">
    <div class="card card-body bg-light">
      <div class="title">:: Todolist App</div>
    </div>
    <div class="card card-default panel-borderless">
      <div class="card-body">
        <TodoFilter :todoList="todoList" @type-filter="typeFilter" />
        <DarkMode @dark-mode="darkMode" />
        <DeleteButton :todoList="todoList" @delete-total="deleteTotal" />
        <InputTodo @addTodo="addTodo" />
        <TodoList
          :todolist="todoList"
          @delete-todo="deleteTodo"
          @toggle-completed="toggleCompleted"
          :filterType="filterType"
        />
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from 'vue';
import TodoList from './components/TodoList.vue';
import InputTodo from './components/InputTodo.vue';
import DeleteButton from './components/DeleteButton.vue';
import DarkMode from './components/DarkMode.vue';
import TodoFilter from './components/TodoFilter.vue';

export default {
  name: 'App',
  components: {
    TodoList,
    InputTodo,
    DeleteButton,
    DarkMode,
    TodoFilter,
  },

  setup() {
    let ts = new Date().getTime();

    const todoList = ref([
      { id: ts, todo: '자전거 타기', completed: false },
      { id: ts + 1, todo: '딸과 공원 산책', completed: true },
      { id: ts + 2, todo: '일요일 애견 카페', completed: false },
      { id: ts + 3, todo: 'Vue 원고 집필', completed: false },
    ]);

    const mode = ref(false);
    const filterType = ref(0);

    const typeFilter = (type) => {
      filterType.value = type;
    };

    const darkMode = (payload) => {
      mode.value = payload;
    };

    const deleteTotal = () => {
      todoList.value = [];
    };

    const addTodo = (todo) => {
      todoList.value.push({
        id: new Date().getTime(),
        todo,
        completed: false,
      });
    };

    const deleteTodo = (id) => {
      const index = todoList.value.findIndex((ele) => id === ele.id);
      todoList.value.splice(index, 1);
    };

    const toggleCompleted = (id) => {
      const index = todoList.value.findIndex((item) => id === item.id);
      todoList.value[index].completed = !todoList.value[index].completed;
    };

    return {
      todoList,
      mode,
      filterType,
      typeFilter,
      darkMode,
      deleteTotal,
      addTodo,
      deleteTodo,
      toggleCompleted,
    };
  },
};
</script>

<style scoped>
.dark-mode {
  background-color: black;
}
.light-mode {
  background-color: white;
}
</style>
