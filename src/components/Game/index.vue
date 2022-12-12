<script setup>
import { ref } from 'vue'

export default { 
  props: {
  step: String,
  question: Object,
  onClickVariant: Function,
  questions: Array,
  }
}

//const percent = Math.round(step / questions.length * 100);

</script>

<template>
  <div>

        <h1>{{questions.question}}</h1>
  </div>
</template>

<style scoped>
@import "./style.scss";
</style>