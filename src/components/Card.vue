<template>
  
    <div>
        <!-- copertina -->
        <img :src="`https://image.tmdb.org/t/p/w185${poster}`" :alt="title">

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
            <span class="info">Voto:</span> {{num}}
        </li>
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
    div{
        li{
            margin-bottom: 10px;

            span.info{
                color: rgb(133, 133, 133);
            }

            img{
                width: 30px;
            }
        }
    }
</style>