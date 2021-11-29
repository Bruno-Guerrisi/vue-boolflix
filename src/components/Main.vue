<template>
  <div class="container">
    
      <ul v-for="(element, i) in Films" :key="`element-${i}`">
          <li>

          </li>
      </ul>
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

</style>
