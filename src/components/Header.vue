<template>
  <div class="conatiner">
    <div class="search-bar">
        <input type="text" 
                placeholder="inserire titolo film"
                v-model.trim="searchUser">

        <button @click="$emit('ClickSearch', searchUser)">search</button>
    </div>
  </div>
</template>

<script>


export default {
    name: 'Header',
    components: {
        
    },
    data() {
        return{
            searchUser: '',
        }
    },
}
</script>

<style lang="scss" scoped>

    div.conatiner{
        height: 50px;
        display: flex;
        padding: 20px;

        div.search-bar{
            height: 20px;
            display: flex;
            align-items: center;

            input{
                width: 150px;
                height: 100%;
            }
            button{
                width: 50px;
                height: 100%;
            }
        }
    }

</style>
