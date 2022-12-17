<template>
  <Game 
    v-bind:question="questions[this.current]"
    @onClickVariant="onClickVariant"
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
      result: 0
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

      console.log(event);
      console.log(index);

      if(this.current < this.questions.length){
        let curQuestion = this.questions[this.current];
        console.log(curQuestion);

        // isCorrect?

        this.current += 1;
      }
      else{
        // end game
      }
      
    },
  },
}
 
</script>

<style scoped>

</style>
