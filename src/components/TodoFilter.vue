<template>
  <div>
    <button @click="typeFilter(0)">전체</button>
    <button @click="typeFilter(1)">완료</button>
    <button @click="typeFilter(2)">미완료</button>
  </div>
</template>

<script setup>
const props = defineProps({
  todolist: { type: Array, required: true },
});

const emit = defineEmits(['type-filter']);

const typeFilter = (type) => {
  emit('type-filter', type);
};
</script>

<style scoped></style>
