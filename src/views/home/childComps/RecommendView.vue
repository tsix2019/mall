<template>
  <div class="recommends">
    <div v-for="item in recommends" class="recom-item">
      <a :href="item.link">
        <img :src="item.image" alt="">
        <p>{{item.title}}</p>
      </a>
    </div>
  </div>
</template>

<script>
  export default {
  name: "RecommendView",
  props:{
    recommends:{
      type:Array,
      default() {
        return [];
      }
    }
  }
  }
</script>

<style scoped>
  .recommends{
    display: flex;
    width: 100%;
    text-align: center;
    font-size: 12px;
    padding: 8px 0 10px;
    border-bottom: 10px solid #eee;
  }
  .recom-item{
    flex: 1;
  }
  .recom-item img {
    width: 60px;
    margin-bottom: 6px;
  }
</style>