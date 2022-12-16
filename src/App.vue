<template>
  <Game/>
</template>

<script>
import Game from './components/Game/index.vue';
export default {
  name: 'app',
  data() {
    return {
      posts: [],
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
        this.posts = data;
        console.log(this.posts);
      });
    }
  },
}
 
</script>

<style scoped>

</style>
