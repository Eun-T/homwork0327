<template>
  <div>
    <button @click="deleteTotal">전체삭제</button>
  </div>
</template>

<script>
export default {
  name: "DeleteButton",
  props: ['todoList'],
  data() {
    return {
    };
  },
  methods: {
    deleteTotal() {
        this.$emit('delete-total',this.todoList.length)
    }
  },
};
</script>

<style scoped>
</style>