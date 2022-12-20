<template>
  <div>
    <div>
      <div class="progress">
        <div :width="`${getProgress()}%`" class="progress__inner"></div>
      </div>
      <h1>{{ question?.question }}</h1>
      <ul>
        <li
          v-for="(item, index) in removeEmpty(question?.answers)"
          :key="index"
          @click="$emit('onClickVariant', item, index)"
        >
          {{ item }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["question", "step", "length"],
  methods: {
    removeEmpty(obj) {
      return Object.fromEntries(
        Object.entries(obj).filter(([_, v]) => v != null)
      );
    },
    getProgress() {
      console.log(Math.round((this.step / this.length) * 100));
      return Math.round((this.step / this.length) * 100);
    },
  },
};
</script>

<style scoped>
@import "./style.scss";
</style>
