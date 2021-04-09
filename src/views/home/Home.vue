<template>
  <div id="home">
    <navbar class="home-nav"><div slot="center">购物盖</div></navbar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature></feature>
    <tab-control :titles="['潮流','新款','推荐']"
                @tabClick="tabCilck">

    </tab-control>
    <goods-iist :goods="showGoods"></goods-iist>
  </div>
</template>

<script>
import Navbar from "@/components/common/navbar/Navbar";
import HomeSwiper from "@/views/home/childComps/HomeSwiper";
import RecommendView from "@/views/home/childComps/RecommendView";
import TabControl from "@/components/content/tabControl/TabControl"
import Feature from "@/views/home/childComps/Feature"
import GoodsIist from "@/components/content/goods/GoodsIist";

import {getHomeMultidata,getHomeGoods} from "@/network/home";

export default {
  name: "Home",
  data(){
    return {
      banners:[],
      recommends:[],
      goods:{
        'pop':{page:0,list:[]},
        'new':{page:0,list:[]},
        'sell':{page:0,list:[]}
      },
      currentType:'pop'
    }
  },
    components: {
      Navbar,
      HomeSwiper,
      RecommendView,
      Feature,
      GoodsIist,
      TabControl
    },
  created() {
    this.getHomeMultidata();
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  methods:{
    getHomeMultidata(){
      getHomeMultidata().then( res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
        // console.log(this.banners)
        // console.log(this.recommends)
      })
    },
    getHomeGoods(type){
      const page = this.goods[type].page + 1
      getHomeGoods(type,page).then( res => {
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1
      })
    },
    tabCilck(index){
      if(index === 0){
        this.currentType = 'pop'
      }else if(index === 1){
        this.currentType = 'new'
      }else if(index === 2){
        this.currentType = 'sell'
      }
    }
  },
  computed:{
    showGoods(){
      return this.goods[this.currentType].list
    }
  }

}


</script>

<style scoped>
  .home-nav{
    background: var(--color-tint);
    color:#ffffff;
  }
</style>