<template>
  <div class="search-section">
    <h1 class="main-title">Home</h1>
    <div class="search-wrapper">
        <input id="search-input" type="text" placeholder="  Type here your search" v-model="user_value">
    </div>
    <div class="search-btn" @click="$emit('search_input',user_value)">Search</div>

    <!-- <div class="search-btn" @click="data_fetch">Search</div> -->
  </div>
</template>

<script>
export default {
    data(){
        return{
            user_value:''
        }
    },

    emits:['search_input']
}

</script>

<style scoped>
.main-title{
        color: rgba(27, 43, 58, 1);
        text-align: center;
        text-decoration: underline;
    }

    .search-btn{
    background-color: rgba(0, 182, 127, 1);
    padding: 10px;
    border-radius: 20px;
    margin-left: 120px;
    margin-top: 20px;
    text-align: center;
    width: 30%;
    font-size: 12px;;
    
  } 

  .search-wrapper{
        display: flex;
        margin: 30px;
       
    }
  .search-section{
    margin: 20px;
  }
    #search-input{
        width: 100%;
        height: 2.8rem;
        outline: none;
        border: 1px solid rgba(27, 43, 58, 1);
        border-radius: 40px;
        padding: 5px 20px;
        font-size: 1rem;
        background: white url(../assets/search.svg) left no-repeat;
        background-size: 25px;
    }

</style>