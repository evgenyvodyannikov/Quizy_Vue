<script setup>
import Game from './components/Game/index.vue';
import { ref } from "vue";


var url = new URL('https://quizapi.io/api/v1/questions');
var params = [['apiKey', 'F2vPTpqtEbEd9489JM5TeVayeUohhXF5hbnXw2iS'], ['limit', '9']]; // , ['category', 'Linux']

url.search = new URLSearchParams(params).toString();

fetch(url)
  .then(res => res.json())
  .then((data) => {
    console.log(data);
    questions.value = data;
    console.log(questions);
    isFetched.value = true;
  })
  .catch("Ошибка получения данных с сервера.\nПерезагрузите страницу.");

const questions = ref([]);
let isFetched = ref(false);

</script>

<template>
  <Game :questions=questions />
</template>

<style scoped>

</style>
