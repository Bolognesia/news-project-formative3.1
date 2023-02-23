<script setup>
  import HeaderVue from './components/Header.vue'
  import HeroVue from './components/Hero.vue'
  import MainVue from './components/Main.vue'
  import SearchVue from './components/Search.vue'
</script>

<template>
  <HeaderVue />
  <HeroVue  :hero_article_obj='my_news_array[my_news_array.length-1]' />
  <SearchVue />
  <MainVue :article_array='my_news_array' />
 
</template>


<style scoped>

</style>

<script>
    export default {
    data(){ // data itself starts
        return{ // data variables starts
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
        ]
        } // data variables end
    }, // data itself ends

    methods:{ // funtions are written in methods
        async data_fetch(){
        const response = await fetch("https://newsapi.org/v2/everything?q=entertainment||business||technology||movies&from=2023-02-01&to=2023-02-22&sortBy=popularity&language=en&apiKey=80ba26a4dfe64eeeb8acbcf0ae02a6ee");
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
        this.data_fetch();
    } // end of created
    }
</script>

