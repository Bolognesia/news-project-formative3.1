<template>
    <div class="hero-img-wrapper">
        <img :src="hero_article_obj.urlToImage" alt="">
    </div>
    <div class="title-wrapper">
        <h1>{{hero_article_obj.title}}</h1>
    </div>
</template>

<style scoped>
    .hero-img-wrapper{
        width:100%;
        height: 200px;
    }

    img{
        width: 100%;
        height: 100%;
        object-fit:cover;
    }

    .title-wrapper{
        background-color: rgba(27, 43, 58, 1);
        color: white;
        padding: 20px 10px;
    }

    h1{
        font-size: 20px;
        text-align: right;
        
    }
</style>

<script setup>
   //Hero prop declaration starts
   defineProps({
     hero_article_obj: { 
       type: Object, 
       required: true
     },
   });
   //Hero pro declaration ends
</script>

