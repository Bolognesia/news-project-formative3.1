<script setup>
  import HeaderVue from './components/Header.vue'
  import HeroVue from './components/Hero.vue'
  import MainVue from './components/Main.vue'
  import FooterVue from './components/Footer.vue'
  import SearchVue from './components/Search.vue'
</script>

<template>
  <HeaderVue />
  <HeroVue  
  :hero_article_obj='my_news_array[my_news_array.length-1]' 
  v-if="search_happened"
  />
  

  <!-- <div class="search-section">
    <h1 class="main-title">Home</h1>
    <div class="search-wrapper">
        <input id="search-input" type="text" placeholder="  Type here your search" v-model="user_input">
    </div>
    <div class="search-btn" @click="data_fetch">Search</div>
  </div> -->
<SearchVue @search_input="data_fetch"/>
  

  <h1 class="main-title">Categories</h1>
  <div class="categories-section">
    
    <div class="single-category-wrapper" v-for="category in main_categories" :main_categories="category" >
      <a href="#loading" class="categories"><h4 @click="user_input=category.category_name;data_fetch()">{{ category.category_name }}</h4></a>
        
        
        <!-- <div class="category-img-wrapper">
          <img class="category-logo" :src="category.category_img" alt="">
        </div> -->
    </div>
  </div>

  <div id="loading" class="loader" v-if="my_news_array.length==1 && search_happened"></div>
  <MainVue 
  :article_array='my_news_array'
  v-if="search_happened" />

  

  <FooterVue />
</template>


<style scoped>
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

  .categories-section{
    display: flex;
    flex-direction: column;
  }


  .single-category-wrapper{
    display: flex;
    align-items: center;
    max-height: 50px;
    background-color: rgba(0, 182, 127, 1);
    margin: 10px;
    color: rgba(27, 43, 58, 1);
    padding: 8px;
    border-radius: 20px;
  }

  .category-img-wrapper{
    width: 100px;
    height: 100px;
  }

  .category-logo{
    width: 100%;
    height: 100%;
    object-fit:fill;
  }

  .loader {
        border: 16px solid #f3f3f3;
        border-radius: 50%;
        border-top: 16px solid #3498db;
        width: 120px;
        height: 120px;
        -webkit-animation: spin 2s linear infinite; /* Safari */
        animation: spin 2s linear infinite;
        align-self: center;
        margin: auto;
    }

    @-webkit-keyframes spin {
        0% { -webkit-transform: rotate(0deg); }
        100% { -webkit-transform: rotate(360deg); }
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }

    .categories{
      text-decoration: none;
      color: rgba(27, 43, 58, 1);
    }
</style>

<script>
    export default {
    

    data(){ // data itself starts
        return{ // data variables starts
        user_input: '',
        sort_by: '',
        main_categories:[
          {
            category_name: 'Entertainment',
            category_img: './assets/entertainment.svg'
          },
          {
            category_name: 'Business',
            category_img: './assets/business.svg'
          },
          {
            category_name: 'Technology',
            category_img: './assets/tech.svg'
          },
          {
            category_name: 'Politics',
            category_img: './assets/politics.svg'
          },
        ],
        my_news_array:[
          {
            author:'',
            content:'',
            title:'',
            description:'',
            url:'',
            urlToImage:'',
            source:{
              name:'',
              id:''
            }
          }
        ],
        search_happened: false,
        } // data variables end
    }, // data itself ends



    methods:{ // funtions are written in methods
        async data_fetch(){
        this.search_happened = true;
        const response = await fetch("https://newsapi.org/v2/everything?q="+this.user_input+"&from=2023-02-01&to=2023-02-22&sortBy=popularity&language=en&apiKey=80ba26a4dfe64eeeb8acbcf0ae02a6ee");
        const received_data = await response.json();
        // at this point our data is available under received_data variable
        // console.log( received_data );
        this.my_news_array = received_data.articles;
        // console.log(this.my_news_array[0]);
        // console.log(received_data.articles);
        // console.log(this.my_news_array[this.my_news_array.length-1]);
        // console.log(this.my_news_array);
        
        }
    }, // methods end

    created(){ // created() is where initial code runs once
        // this.data_fetch();
    } // end of created
    }
</script>

