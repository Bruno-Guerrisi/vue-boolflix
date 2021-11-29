<template>
  
    <div>
        <li>{{title}}</li>
        <li>{{subTitle}}</li>
        <img v-if="arrOn == true" :src="`@/assets/img/${language}.png`" alt="">
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
    },
    data(){
      return {

          arrLanguage: ['en', 'it'],
      }
    },
    computed: {

        arrOn () {
        return this.arrLanguage.includes(this.language);
    }
    }
}
</script>

<style lang="scss">

</style>