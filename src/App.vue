<template>
  <div id="app">
    
    <header>
      <Header @ClickSearch='Result' />
    </header>

    <main>
      <Main :Films="listFilms"/>
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';

export default {
  name: 'App',

  components: {
    Header,
    Main,
  },

  data() {
    return {
      listFilms: null,
      SearchResult: '',
    }
  },

  methods: {

    getListFilm(){

      if (this.SearchResult != '') {

        axios.get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: '39c71b5436e3551a0f94369219cc87ba',
            query: this.SearchResult,
            language: 'it-IT',
          },
        })

        .then(result => {
          this.listFilms = result.data.results;
          console.log(result.data);
        })
        .catch(error => {
          console.log(error);
        })
      } else {
        this.listFilms = null;
      }
    },

    Result(text){
      this.SearchResult = text;

      this.getListFilm();
    },
  },
}

</script>

<style lang="scss">
@import '@/style/globals';

  #app{
    background-color: rgb(19, 19, 63);
    min-height: 100vh;
    
      header{
        background-color: rgb(28, 28, 97);
      }

      main{
        color: white;
        padding: 20px;
      }
  }

</style>
