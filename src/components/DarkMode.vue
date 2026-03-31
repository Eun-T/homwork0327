<template>
  <div>
    <i
      :class="{ hidden: this.mode }"
      class="fa-solid fa-moon fa-2x"
      @click="darkMode"
    ></i>
    <i
      :class="{ hidden: !this.mode }"
      class="fa-regular fa-moon fa-2x"
      @click="darkMode"
    ></i>
  </div>
</template>

<script>
import { ref } from 'vue';

// 내꺼
// if(now >= 6 && now < 18){
//     this.mode = true
// }
export default {
  setup(props, { emit }) {
    const now = new Date().getHours();
    const mode = ref(!(now >= 6 && now < 18));

    const darkMode = () => {
      mode.value = !mode.value;
      emit('dark-mode', mode.value);
    };

    return {
      mode,
      darkMode,
    };
  },
};
</script>

<style scoped>
.hidden {
  display: none;
}
</style>
