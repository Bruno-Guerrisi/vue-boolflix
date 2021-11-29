<template>
  
    <div>
        <li v-if="repeaTitle == false">{{title}}</li>
        <li>{{subTitle}}</li>
        <li>{{date}}</li>

        <li v-if="arrOn == true">
            <img :src="require(`@/assets/img/${language}.png`)" 
                :alt="title">
        </li>
        <li v-else>{{language}}</li>

        <li>{{num}}</li>
    </div>

</template>

<script>

export default {
    name: 'Card',
     props:{

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
        return this.title == this.subTitle;
        },
    }
}
</script>

<style lang="scss">
    div{
        li{
            margin-bottom: 5px;

            img{
                width: 30px;
            }
        }
    }
</style>