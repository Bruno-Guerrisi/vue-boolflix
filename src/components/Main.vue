<template>
  <div class="container">
    

    <div v-if="Films != null || Series != null" class="main-container-all">

        <div class="select-genres">

            <button class="films-list" 
                    @click="editFilms" 
                    :class="{red: addFilms == false,
                            green: addFilms == true }">
                    Film: {{Films.length}}
            </button>

            <button class="series-list" 
                    @click="editSeries" 
                    :class="{red: addSeries == false,
                            green: addSeries == true }">
                    Serie Tv: {{Series.length}}
            </button>
        </div>

        <div class="container-films-series">

            <!-- films -->
            <h2 class="name-section" v-if="addFilms == true">Film</h2>
            <div class="container-films" v-if="addFilms == true">

                <ul class="film" v-for="(element, i) in Films" :key="`film-${i}`">
                    
                    <Card :poster="element.poster_path"
                    :title="element.title" 
                    :subTitle="element.original_title" 
                    :language="element.original_language" 
                    :num="element.vote_average"
                    :description="element.overview"
                    :date="element.release_date" />
                </ul>
            </div>

            <!-- series -->
            <h2 class="name-section" v-if="addSeries == true">Serie TV</h2>
            <div class="container-series" v-if="addSeries == true">
                <ul class="film" v-for="(element, i) in Series" :key="`serie-${i}`">
                    
                    <Card :poster="element.poster_path"
                    :title="element.name"
                    :subTitle="element.original_name" 
                    :language="element.original_language" 
                    :num="element.vote_average"
                    :description="element.overview"
                    :date="element.first_air_date" />
                </ul>
            </div>

            <span v-if="addFilms == false && addSeries == false">
                Selezionare almeno un genere da visualizzare
            </span>
        </div>
    </div>

    <div v-else-if="Films == null && Series == null && SearchResult == '' ">

        <span>Inserire il nome di una serie tv o un film</span>
    </div>

    <div v-else-if="Films == null || Series == null && SearchResult != '' " 
          class="container loading">

        <div class="loading-box"></div>
        <span>Loading...</span>
    </div>


  </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'Main',
    props:{

        Films: Array,
        Series: Array,
        SearchResult: String,
    },
    data() {
        return{

            addFilms: true,
            addSeries: true,
        }
    },
    components: {
        Card,
    },
    methods: {

        editFilms(){

            if (this.addFilms == false) {
                this.addFilms = true;
            } else{
                this.addFilms = false;
            }
        },

        editSeries(){

            if (this.addSeries == false) {
                this.addSeries = true;
            } else{
                this.addSeries = false;
            }
        },
    }
}
</script>

<style lang="scss" scoped>

    div.container{

        .select-genres{

            display: flex;
            justify-content: center;

            button {
                margin: 0 10px;
                border-radius: 5px;
                padding: 5px;
                cursor: pointer;
                border: 0;
                background-color: rgba(43, 43, 43);
                transition: transform 0.1s;

                &:hover{
                    transform: scale(1.1);
                }
            }

            button.red{
                color: red;
            }
            button.green{
                color: green;
            }

        }


        div.container-films-series{

            display: flex;
            flex-direction: column;
            align-items: center;

            span{
                margin-top: 20px;
            }

            h2.name-section{
                margin-top: 20px;
                margin-bottom: 10px;
            }

            div.container-films,
            div.container-series{
    
                display: flex;
                width: 100%;
                justify-content: center;
                overflow-y: auto;
                align-items: center;
                flex-wrap: wrap;
    
    
                ul.film{
    
                    padding: 20px;
                    // max-width: calc(100% / 4);
                    
    
                    div{
    
                        display: flex;
                        flex-direction: column;
                        align-items: center;
    
                    }
                }
            }
        }


        /* caricamento */
        div.container.loading{

            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;

            div.loading-box{

                width: 50px;
                height: 50px;
                border: 3px solid white;
                border-radius: 50%;
                border-top: 3px solid transparent;
                animation: rotate 1s linear infinite;

                @keyframes rotate {
                    0%{
                        transform: rotate(0deg);
                    }
                    100%{
                        transform: rotate(360deg);
                    }
                }
            }

            span{
                color:white;
                margin-top: 20px;
                font-weight: bold;
            }
        }
    }

    /* @media screen and (max-width: 1000px) {

        div.container{

            div.container-films-series{

                ul.film{

                    padding: 20px;
                    width: calc(100% / 3);

                }
            }
        }
    }

    @media screen and (max-width: 850px) {

        div.container{

            div.container-films-series{

                ul.film{

                    padding: 20px;
                    width: calc(100% / 2);

                }
            }
        }
    }

    @media screen and (max-width: 800px) {

        div.container{

            div.container-films-series{

                ul.film{

                    padding: 20px;
                    width: 100%;

                }
            }
        }
    } */

</style>
