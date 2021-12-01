<template>
  <div class="conatiner">


    <a class="logo" href="#">
        <img src="@/assets/img/logo.png" alt="">
    </a>

    <div class="user-section">

        <div class="search-bar">
            <input type="text" 
                    placeholder="inserire titolo film"
                    v-model.trim="searchUser"
                    @keyup.enter="$emit('ClickSearch', searchUser)">

            <button @click="$emit('ClickSearch', searchUser)">search</button>
        </div>

        <div class="language">
            <select v-model.trim="Language"  
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
        height: 70px;
        display: flex;
        padding: 10px;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .logo{
            display: flex;
            align-items: center;
            
            img{

                
                width: 70%;
            }
        }


        .user-section{
            display: flex;

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
    
            div.language{
                
                select{
                    min-width: 50px;
                }
            }
        }
    }

</style>
