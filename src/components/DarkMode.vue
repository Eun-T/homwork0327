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
// 내꺼
// if(now >= 6 && now < 18){
//     this.mode = true
// }
export default {
  name: 'DarkMode',
  data() {
    //처음 실행했을때 06시부터 18시 사이면 라이트모드로
    const now = new Date().getHours()
    return {
      mode: !(now >= 6 && now < 18),
    };
  },
  methods: {
    darkMode(payload) {
      this.mode = !this.mode;
      this.$emit('dark-mode', this.mode);
    },
  },
};
</script>

<style scoped>
.hidden {
  display: none;
}
</style>
