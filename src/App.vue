<template>
    <div id="app">
        
        <header>
            <Header @ClickSearch='Result' @selectLanguage='currentLanguage' />
        </header>

        <main>
            <Main :Films="listFilms"
                 :Series="listSeries"
                 :SearchResult="SearchResult"/>
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
            listSeries: null,
            SearchResult: '',
            Language: 'it-IT',
        }
    },

    methods: {

        getListFilm(){

            if (this.SearchResult != '') {

                /* film */
                axios.get('https://api.themoviedb.org/3/search/movie', {
                    params: {
                        api_key: '39c71b5436e3551a0f94369219cc87ba',
                        query: this.SearchResult,
                        language: this.Language,
                    },
                })

                .then(result => {
                    this.listFilms = result.data.results;
                    console.log(result.data);
                })
                .catch(error => {
                    console.log(error);
                })

                /* serie tv */
                axios.get('https://api.themoviedb.org/3/search/tv', {
                    params: {
                        api_key: '39c71b5436e3551a0f94369219cc87ba',
                        query: this.SearchResult,
                        language: this.Language,
                    },
                })

                .then(result => {
                    this.listSeries = result.data.results;
                    console.log(result.data);
                })
                .catch(error => {
                    console.log(error);
                })
            }
            else {
                this.listFilms = null;
                this.listSeries = null;
            }
        },

        currentLanguage(text){
            this.Language = text;

            this.getListFilm();
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
        background-color: rgb(24, 24, 24);
        min-height: 100vh;
        min-width: 400px;
        
        header{
            background-color: rgb(43, 43, 43);
            position: fixed;
            width: 100%;
            z-index: 1;
        }

        main{
            color: white;
            padding: 80px 20px 20px 20px;
        }
    }

</style>
