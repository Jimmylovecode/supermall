<template>
<div id="home" class="wrapper">
<nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
<tab-control :titles="['流行','新款','精选']" class="tab-control" @tabClick='tabClick' ref="tabControl1" v-show="isTabFixed" ></tab-control>
<scroll class="content" ref="scroll" :probe-type="3" @scroll="contentScroll" :pull-up-load="true" @pullingUp ="loadMore">
<home-swiper :banners="banners" @imageLoad="swiperImageLoad"/>
<recommend-view :recommends="recommends"/>
<feature-view/>
<tab-control :titles="['流行','新款','精选']" class="tab-control" @tabClick='tabClick' ref="tabControl2"></tab-control>
<goods-list :goods="goods[currentType].list" />
</scroll>
<back-top @click.native="backClick" v-show="isBackTop"/>
</div>
</template>

<script>

import NavBar from '../../components/common/navbar/NavBar.vue'
import Scroll from '../../components/common/scroll/Scroll.vue'
import BackTop from '../../components/content/backTop/BackTop.vue'
import GoodsList from '../../components/content/goods/GoodsList.vue'
import TabControl from '../../components/content/tabControl/TabControl.vue'
import {getHomeMultidata,getHomeGoods} from "../../network/home"
import FeatureView from './childComps/FeatureView.vue'
import HomeSwiper from './childComps/HomeSwiper.vue'
import RecommendView from './childComps/RecommendView.vue'
import {debounce} from "../../common/utils.js"
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
          FeatureView,
          TabControl,
          GoodsList,
          Scroll,
                BackTop,
        },
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
            currentType:"pop",
            isBackTop:false,
            tabOffsetTop:0,
            isTabFixed:false,
            saveY:0
          }
        },
        activated(){
          this.$refs.scroll.scroll.scrollTo(0,this.saveY,0)
          this.$refs.scroll.refresh()
        },
        deactivated(){
          this.saveY = this.$refs.scroll.scroll.y
        },
        created(){
          getHomeMultidata().then(res =>{
            this.banners = res.data.banner.list;
            this.recommends = res.data.recommend.list
          })
          this.getHomeGoods('pop')
          this.getHomeGoods('new')
          this.getHomeGoods('sell')
          
          //监听图片加载完成
      /*     this.$bus.$on('itemImgLoad', () => {
            this.$refs.scroll.refresh()
          }) */
        },
        mounted(){
          //1.图片加载完成的监听
          const refresh = debounce(this.$refs.scroll.refresh,500)
          this.$bus.$on('itemImgLoad', () => {
            refresh()
          })
        },
        methods:{
          tabClick(index){
            switch(index){
              case 0:
                this.currentType = 'pop'
                break
              case 1:
                this.currentType = 'new'
                break
              case 2:
                this.currentType = 'sell'
                break
            }
            this.$refs.tabControl1.currentIndex = index
            this.$refs.tabControl2.currentIndex = index
          },
          getHomeGoods(type){
            const page = this.goods[type].page + 1
            getHomeGoods(type,page).then(res => {
              this.goods[type].list.push(...res.data.list)
              this.goods[type].page += 1
              this.$refs.scroll.scroll.finishPullUp()
            })
          },
          backClick(){
            this.$refs.scroll.scroll.scrollTo(0,0,500)
          },
          contentScroll(position){
            this.isBackTop = (-position.y) > 1000,
            this.isTabFixed = (-position.y) > this.tabOffsetTop
          },
          loadMore(){
            this.getHomeGoods(this.currentType)
          },
          swiperImageLoad(){
            this.tabOffsetTop = this.$refs.tabControl2.$el.offsetTop;
          }
        }
    }
</script>

<style scoped>
#home{
  padding-top:44px;
  position: relative;
  height: 100vh;
}
.home-nav{
  background-color: var(--color-tint);
  color:#fff;
  position:fixed;
  left:0;
  right:0;
  top:0;
  z-index: 9;
}
.tab-control{
  position:sticky;
  top:44px;
  background-color: #fff;
  z-index: 9;
}
.content{

  position:absolute;
  top:44px;
  bottom:49px;
  left:0;
  right: 0;
  
}
</style>




