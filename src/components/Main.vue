<template>
  <div class="container">
    

    <div v-if="Films != null || Series != null" class="main-container-all">

        <!-- films -->
        <ul class="film" v-for="(element, i) in Films" :key="`film-${i}`">
            
            <Card :poster="element.poster_path"
            :title="element.title" 
            :subTitle="element.original_title" 
            :language="element.original_language" 
            :num="element.vote_average"
            :description="element.overview"
            :date="element.release_date" />
        </ul>

        <!-- series -->
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
    components: {
        Card,
    },
}
</script>

<style lang="scss" scoped>

    div.container{


        div.main-container-all{

            display: flex;
            flex-wrap: wrap;
            justify-content: center;

            ul.film{

                padding: 20px;
                width: calc(100% / 4);

                div{

                    display: flex;
                    flex-direction: column;
                    align-items: center;

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

</style>
