<template>
    
    <ArticleModalVue
        :single_article="modal_prop"
        @click="modal_on=false"
        v-if="modal_on"
    />

    <h1 class="main-title">Articles</h1>
    <div class="main-wrapper">
        <ArticleVue 
            v-for="single_article in article_array"
            :single_article_obj="single_article" 
            @click="modal_load(single_article)"
        />
    </div>

</template>

<style scoped>
  
    .main-title{
        color: rgba(27, 43, 58, 1);
        text-align: center;
        text-decoration: underline;
    }



</style>

<script setup>
    //Article prop declaration starts
    import ArticleVue from './Article.vue'
    import ArticleModalVue from './ArticleModal.vue'

   defineProps({
    article_array: { 
       type: Array, 
       required: true
     },
   });
   
   //Article prop declaration ends
</script>

<script>
    export default {
    data(){ // data itself starts
        return{ // data variables starts
        modal_prop:{
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
          },
        modal_on:false,  
        } // data variables end
    }// data itself ends
    ,

    methods:{
        modal_load(parameterObj){
            this.modal_on=true;
            this.modal_prop=parameterObj;
            console.log(this.modal_load);
        }
    }
}     
</script>