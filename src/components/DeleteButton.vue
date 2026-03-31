<template>
  <div>
    <button @click="deleteTotal">전체삭제</button>
  </div>
</template>

<script>
export default {
  // name: 'DeleteButton',
  props: ['todoList'],
  setup(props, { emit }) {
    const deleteTotal = () => {
      emit('delete-total', props.todoList.length);
    };

    return {
      deleteTotal,
    };
  },
};
</script>

<style scoped></style>
