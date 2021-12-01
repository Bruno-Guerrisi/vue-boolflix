<template>
  
    <div class="container-list">
        <!-- copertina -->
        <img v-if="poster != null || poster != undefined" 
            :src="`https://image.tmdb.org/t/p/w342${poster}`" 
            :alt="title"
            class="porster">

        <div class="no-poster porster" v-else>No image</div>

        <div class="info-list">

            <li v-if="repeaTitle == false">
                <span class="info">Titolo:</span> {{title}}
            </li>

            <li>
                <span class="info">Titolo originale:</span> {{subTitle}}
            </li>

            <li>
                <span class="info">Data:</span> {{date}}
            </li>

            <li v-if="arrOn == true">
                <span class="info">Lingua: </span>
                <img :src="require(`@/assets/img/${language}.png`)" 
                    :alt="title">
            </li>
            <li v-else>
                <span class="info">Lingua:</span> {{language}}
            </li>

            <li>
                <span class="info">Voto:</span>

                <i v-for="(n , i) in Math.ceil(num / 2)" 
                    :key="`starOne-${i}`" 
                    class="fas fa-star starOne"></i>

                <i v-for="(n , i) in  (5 - Math.ceil(num / 2))" 
                    :key="`starTwo-${i}`" 
                    class="far fa-star starTwo"></i>

            </li>

            <li v-if="description != '' " class="overview">
                <span class="info">Overview:</span> {{description}}
            </li>

            <li v-else class="overview">
                <span class="info">Overview:</span> No description
            </li>
        </div>
    </div>

</template>

<script>

export default {
    name: 'Card',
    props:{

        poster: String,
        title: String,
        subTitle: String,
        language: String,
        num: Number,
        date: String,
        description: String,
    },
    data(){
      return {

        arrLanguage: ['en', 'it'],
      }
    },
    computed: {

        arrOn () {
            return this.arrLanguage.includes(this.language);
        },

        repeaTitle () {
            return this.title.replace(/ /g, "").toLowerCase() 
            == 
            this.subTitle.replace(/ /g, "").toLowerCase();
        },
    }
}
</script>

<style lang="scss">
    div.container-list{

        position: relative;
        cursor: pointer;

        &:hover div.info-list{
            display: block;
        }

        &:hover::before{
            content: '';
            background-color: rgba(0, 0, 0, 0.815);
            width: 100%;
            height: 100%;
            display: block;
            position: absolute;
        }


        .no-poster{
            width: 185px;
            height: 277px;
            background-color: rgb(73, 73, 73);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
        }

        div.info-list{

            position: absolute;
            padding: 10px;
            margin-bottom: 10px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            max-width: 95%;
            min-width: 90%;
            max-height: 90%;
            overflow-y: auto;
            display: none;

            li{

                list-style: none;

                margin-bottom: 10px;
    
                span.info{
                    color: rgb(133, 133, 133);
                }
    
                img{
                    width: 30px;
                }
    
                .starOne{
                    color: yellow;
                }
                .starTwo{
                    color: gray;
                }
            }
        }
    }
</style>