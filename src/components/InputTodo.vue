<template>
  <div class="row mb-3">
    <div class="col">
      <div class="input-group">
        <input
          type="text"
          class="form-control"
          placeholder="할일을 여기에 입력!"
          v-model="todo"
          @keyup.enter="addTodoHanlder"
        />
        <button class="btn btn-primary" type="button" @click="addTodoHanlder">
          추가
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue';

  const todo = ref('')
  
  const emit = defineEmits(['addTodo']);

   const addTodoHanlder = () => {
      if (todo.value.length >= 3) {
        emit('addTodo', todo.value);
        todo.value = '';
        return; 
      }
      alert('할 일은 3글자 이상 입력해주세요.');
    };

</script>


