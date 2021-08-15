<template>
<div id="home">
<nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
<home-swiper :banners="banners"/>
<recommend-view :recommends="recommends"/>
</div>
</template>

<script>

import NavBar from '../../components/common/navbar/NavBar.vue'
import {getHomeMultidata} from "../../network/home"
import HomeSwiper from './childComps/HomeSwiper.vue'
import RecommendView from './childComps/RecommendView.vue'
/* import Swiper from "../../components/common/swiper/Swiper.vue"
import SwiperItem from "../../components/common/swiper/SwiperItem.vue" */
/* import {Swiper,SwiperItem} from '../../components/common/swiper/index' */
/* import Swiper from '../../components/common/swiper/Swiper.vue'
import SwiperItem from '../../components/common/swiper/SwiperItem.vue' */
    export default {
        components: { 
          NavBar,
          HomeSwiper,
          RecommendView,
        },
        name: "Home",
        data(){
          return {
            banners:[],
            recommends:[]
          }
        },
        created(){
          getHomeMultidata().then(res =>{
            this.banners = res.data.banner.list;
            this.recommends = res.data.recommend.list
          })
        }
    }
</script>

<style scoped>
.home-nav{
  background-color: var(--color-tint);
  color:#fff
}
</style>



</style>
