<template>
  <div class="conatiner">
    <div class="search-bar">
        <input type="text" 
                placeholder="inserire titolo film"
                v-model.trim="searchUser">

        <button @click="$emit('ClickSearch', searchUser)">search</button>
    </div>

    <div class="language">
        <select name="Language" 
                v-model.trim="Language"  
                @change="$emit('selectLanguage', Language)">

            <option value="it-IT">Italian</option>
            <option value="en-EN">English </option>
            <option value="fr-FR">French </option>
            <option value="es-ES">Spanish</option>
            <option value="de-DE">German</option>
            <option value="zh-ZH">Chinese</option>
            <option value="ja-JA">Japanese</option>
            <option value="ar-AR">Arabic</option>
        </select>
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
            Language: '',
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
