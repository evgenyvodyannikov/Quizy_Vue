<template>
  <div>
    <div class="Game">
      <h1>{{ question?.question }}</h1>
      <ul>
        <li v-for="(item, index) in removeEmpty(question?.answers)" v-if="item != ''" :key="index">
          {{ item }}
        </li>
      </ul>
    </div>

  </div>
</template>

<script>
export default {
  props: ['question'],
  methods: {
    removeEmpty(obj) {
      return Object.fromEntries(Object.entries(obj).filter(([_, v]) => v != null));
    }
  }
}
</script>

<style scoped>
@import "./style.scss";
</style>