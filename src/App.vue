<template>
  <Game 
    v-bind:question="questions[this.current]"
    @onClickVariant="onClickVariant"
    v-if="isGameActive"
  />
</template>

<script>
import Game from './components/Game/index.vue';
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
    Game
  },
  methods: {
    fetchData() {

      const url = new URL('https://quizapi.io/api/v1/questions');
      const params = [['apiKey', 'F2vPTpqtEbEd9489JM5TeVayeUohhXF5hbnXw2iS'], ['limit', '9']]; // , ['category', 'Linux']
      
      url.search = new URLSearchParams(params).toString();

      fetch(url)
      .then(response => response.json())
      .then(data => {
        this.questions = data;
        console.log(this.questions);
      });
    },

    onClickVariant(event, index) {

      if(this.current < this.questions.length){
        let curQuestion = this.questions[this.current];
       
        console.log(curQuestion);
        console.log(index);

        if (curQuestion.correct_answers[`${index}_correct`]) this.score++;
        this.current += 1;

        console.log(curQuestion.correct_answers[`${index}_correct`]);
        console.log(this.score);
      }
      else{
        this.isGameActive = false;
      }
    },
  },
}
 
</script>

<style scoped>

</style>
