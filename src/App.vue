<template>
  <div class="App">

    <Game 
      v-bind:question="questions[this.current]"
      @onClickVariant="onClickVariant"
      v-if="isGameActive"
    />

    <Result
      v-bind:score="score"
      v-bind:length="questions.length"
      v-if="!isGameActive"
    />

  </div>
  

</template>

<script>

import Game from './components/Game/index.vue';
import Result from './components/Result/index.vue';

export default {
  name: 'app',

  data() {
    return {
      questions: [],
      current: 0,
      score: 0,
      isGameActive: true,
    }
  },

  created() {
    this.fetchData();
  },

  components: {
    Game,
    Result
  },
  
  methods: {
    fetchData() {

      const url = new URL('https://quizapi.io/api/v1/questions');
      const params = [['apiKey', 'F2vPTpqtEbEd9489JM5TeVayeUohhXF5hbnXw2iS'], ['limit', '10']]; // , ['category', 'Linux']
      
      url.search = new URLSearchParams(params).toString();

      fetch(url)
      .then(response => response.json())
      .then(data => {
        this.questions = data;
        console.log(this.questions);
      });
    },

    onClickVariant(_, index) {

      this.current += 1;

      if(this.current < this.questions.length){
        let curQuestion = this.questions[this.current];
        if (curQuestion.correct_answers[`${index}_correct`] === 'true') this.score++;
      }
      else{
        this.isGameActive = false;
      }
    },
  },
}
 
</script>

<style scoped>
@import "./style.scss";
</style>
