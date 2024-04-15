<script>
export default {
    name: 'AppCard',
    props: ["cardInfo"]
    
}
</script>

<template>
  <div class="my-container">
    <div class="card m-3" >
      <img :src="cardInfo.card_images[0].image_url_small" class="card-img-top" :alt="cardInfo.name">
      <div class="card-body">
        <p class="card-text text-center">{{ cardInfo.name }}</p>
        <div class="text-center">{{ cardInfo.archetype }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .my-container{
    width: calc(100% / 4);
    p, div.text-center{
      font-size: 12px;
    }
  }

  .img{
    width: 100%;
  }

  .card-body{
    height: 100px;
  }
</style>