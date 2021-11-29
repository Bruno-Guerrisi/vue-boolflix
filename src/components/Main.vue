<template>
  <div class="container">
    
    <div class="films">
        <ul v-for="(element, i) in Films" :key="`element-${i}`">
            <li>{{element.title}}</li>
            <li>{{element.original_title}}</li>
            <li>{{element.original_language}}</li>
            <li>{{element.vote_average}}</li>
        </ul>
    </div>

  </div>
</template>

<script>


export default {
  name: 'Main',
  props:{

    Films: Array,
  },
  components: {
    
  },
}
</script>

<style lang="scss" scoped>
    div.container{

        div.films{

            ul{

                margin-bottom: 20px;
            }
        }
    }

</style>
