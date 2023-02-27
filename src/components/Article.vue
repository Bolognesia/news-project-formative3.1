
<template>
  
  <div class="single-article-wrapper">
    <div class="single-article-img-wrapper">
      <img :src="single_article_obj.urlToImage" alt="">
    </div>
    <div class="article-content-wrapper">
      <h1 class="article-title">{{single_article_obj.title}}</h1>
      <p class="article-description">{{single_article_obj.description}}</p>
      <div class="read-more-btn" @click="$emit('readMore')">Read More</div>
      <hr class="separator">
    </div>
  </div>

</template>

<style scoped>

  .separator{
    border: 1px solid rgba(105, 126, 157, 1);
  }
  .single-article-wrapper{
    display: flex;
    padding: 0 20px;
  }

  .single-article-img-wrapper{
    flex: 1;
    padding-top: 20px;
    min-height: 150px;
    max-height: 200px;
  }

  img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 10px;
  }

  .article-content-wrapper{
    width: 200px;
    max-width: 300px; 
    padding: 0 0 0 15px;
  }

  .article-title{
    font-size: 18px;
    color: rgba(27, 43, 58, 1);
  }

  .article-description{
    font-size: 14px;
    overflow-wrap: break-word;
    max-height: 180px;
  }
  .read-more-btn{
    background-color: rgba(0, 182, 127, 1);
    padding: 10px;
    border-radius: 20px;
    margin-left: 80px;
    text-align: center;
    width: 50%;
    font-size: 12px;;
    
  } 
</style>


<script setup>
    //Article prop declaration starts
   defineProps({
    single_article_obj: { 
       type: Object, 
       required: true
     },
   });
   //Article prop declaration ends
</script>

<script>
export default {
  emits:['readMore']
}
</script>