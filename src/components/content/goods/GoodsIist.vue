<template>
  <div class="good-list">
    <goods-list-item v-for="item in goods" :goods-item="item"></goods-list-item>
  </div>
</template>

<script>
import GoodsListItem from "@/components/content/goods/GoodsListItem";
  export default {
    name: "Goodslist",
    props:{
      goods:{
        type:Array,
        default(){
          return []
        }
      }
    },
    components:{
      GoodsListItem
    }
  }
</script>

<style scoped>
  .good-list{
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    justify-content: space-around;
  }
</style>