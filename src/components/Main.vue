<template>
  <div class="container">
    

    <ul class="film" v-for="(element, i) in Films" :key="`element-${i}`">
        
        <Card :title="element.title" 
        :subTitle="element.original_title" 
        :language="element.original_language" 
        :num="element.vote_average" />
    </ul>


  </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
  name: 'Main',
  props:{

    Films: Array,
  },
  components: {
    Card,
  },
}
</script>

<style lang="scss" scoped>

    div.container{

        ul.film{

            margin-bottom: 20px;
        }
    }

</style>
