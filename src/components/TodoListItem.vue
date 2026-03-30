<template>
  <li
    v-if="isVisible"
    class="list-group-item"
    :class="{
      'list-group-item-success': todoitem.completed,
    }"
  >
    <input
      type="checkbox"
      class="pointer me-3"
      :checked="todoitem.completed"
      @click="$emit('checkbox-completed', todoitem.id)"
    />

    <span class="pointer" :class="{ 'todo-done': todoitem.completed }">
      {{ todoitem.todo }}
      {{ todoitem.completed ? '(완료)' : '' }}
    </span>
    <span
      class="float-end badge bg-secondary pointer"
      @click="$emit('delete-todo', todoitem.id)"
      >삭제</span
    >
  </li>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  todoitem: { type: Object, required: true },
  filterType: Number,
});

const isVisible = computed(() => {
  if (props.filterType == 0) {
    return true;
  } else if (props.filterType == 1 && props.todoitem.completed) {
    return true;
  } else if (props.filterType == 2 && !props.todoitem.completed) {
    return true;
  }
  return false;
});

</script>

<style scoped></style>
