<template>
  <div id="home">
    <navbar class="home-nav"><div slot="center">购物盖</div></navbar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature></feature>
    <tab-control :titles="['潮流','新款','推荐']"></tab-control>
    <ul>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>666</li>
      <li>999</li>
    </ul>
  </div>
</template>

<script>
import Navbar from "@/components/common/navbar/Navbar";
import HomeSwiper from "@/views/home/childComps/HomeSwiper";
import RecommendView from "@/views/home/childComps/RecommendView";
import TabControl from "@/components/content/tabControl/TabControl"
import Feature from "@/views/home/childComps/Feature"
import {getHomeMultidata,getHomeGoods} from "@/network/home";
export default {
  name: "Home",
  data(){
    return {
      banners:[],
      recommends:[],
      goods:{
        'pop':{page:0,list:[]},
        'news':{page:0,list:[]},
        'sell':{page:0,list:[]}
      }
    }
  },
    components: {
      Navbar,
      HomeSwiper,
      RecommendView,
      Feature,
      TabControl
    },
  created() {
    getHomeMultidata().then( res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
      console.log(this.banners)
      console.log(this.recommends)
    })
    getHomeGoods('pop',1).then( res => {
      console.log(res)
    })
  },

}


</script>

<style scoped>
  .home-nav{
    background: var(--color-tint);
    color:#ffffff;
  }
</style>