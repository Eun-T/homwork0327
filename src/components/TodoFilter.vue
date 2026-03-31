<template>
  <div>
    <button @click="typeFilter(0)">전체</button>
    <button @click="typeFilter(1)">완료</button>
    <button @click="typeFilter(2)">미완료</button>
  </div>
</template>

<script>
export default {
  name: 'TodoFilter',
  props: ['todolist'],
  emits: ['type-filter'],

  setup(props, { emit }) {
    const typeFilter = (type) => {
      emit('type-filter', type);
    };

    return {
      typeFilter,
    };
  },
};
</script>

<style scoped></style>
