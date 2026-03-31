<template>
  <div class="row">
    <div class="col">
      <ul class="list-group">
        <TodoListItem
          v-for="todoitem in todolist"
          :key="todoitem.id"
          :todoitem="todoitem"
          :filterType="filterType"
          @delete-todo="$emit('delete-todo', $event)"
          @checkbox-completed="$emit('toggle-completed', $event)"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';

export default {
  name: 'TodoList',
  props: ['todolist', 'filterType'],
  components: { TodoListItem },
  setup(props) {
    return {
      ...props,
    };
  },
};
</script>

<!-- Options API
export default {
  name: 'TodoList',
  components: {
    TodoListItem,
  },
  props: ['todolist','filterType'], -->
