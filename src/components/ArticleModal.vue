<template>
    <div class="modal">
        <div class="btn-wrapper">
            <div class="close-btn" @click="$emit('close')">X</div>
        </div>
        
        <h3>{{ single_article.title }}</h3>
        <div class="modal-img-wrapper">
            <img :src="single_article.urlToImage" alt="">
        </div>
        <p class="modal-content">{{single_article.content}}</p>
        <a class="link" :href="single_article.url">Read More</a>
        
    </div>
</template>

<style scoped>
    .modal{
        position: fixed;
        top: 5%;
        left: 0.5%;
        margin: 20px;
        padding: 20px;
        background-color: rgba(27, 43, 58, 1);
        color: white;
        border-radius: 10px;
        width: 300px;
        max-height: 600px;
        border: 3px solid rgba(105, 126, 157, 1);

    }

    .modal-content{
        overflow-wrap: break-word;
    }

    h3{
        margin: 0 0 10px 0;
    }

    .link{
        text-decoration: none;
        color: white;
        background-color: rgba(0, 182, 127, 1);
        padding: 12px 20px;
        margin-left: 80px;
        border-radius: 20px;
    }

    .btn-wrapper{
        display: flex;
        justify-content: end;
        margin: 0 0 10px 0;
    }
    .close-btn{
        background-color: rgba(0, 182, 127, 1);
        padding: 10px;
        border-radius: 50%;
        height: 10px;
        width: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
    }


</style>


<script setup>
    defineProps({
        single_article: { 
        type: Object, 
        required: true
        },
   });
</script>

<script>
export default {
  emits:['close']
}
</script>