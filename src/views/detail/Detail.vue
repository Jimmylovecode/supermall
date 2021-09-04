<template>
<div id="detail"> 
    <detail-nav-bar class="detail-nav"/>
    <scroll class="content" ref="scroll">
         <detail-swiper :image-swiper="topImages"/>
         <detail-base-info :goods="goods"></detail-base-info>
         <detail-shop-info :shop="shop"/>
    </scroll>
</div>
</template>

<script>
import DetailNavBar from './childComps/DetailNavBar.vue'
import {getDetail,Goods,Shop} from '../../network/detail.js'
import DetailSwiper from './childComps/DetailSwiper.vue'
import DetailBaseInfo from './childComps/DetailBaseInfo.vue'
import DetailShopInfo from './childComps/DetailShopInfo.vue'
import Scroll from '../../components/common/scroll/Scroll.vue'
export default {
  name:"Detail",
  components: {
       DetailNavBar,
    DetailSwiper,
    DetailBaseInfo,
    DetailShopInfo,
    Scroll
    },
    data(){
        return {
            iid:null,
            topImages:null,
            goods:{},
            shop:{}
        }
    },
    created(){
        this.iid = this.$route.params.iid,
        getDetail(this.iid).then(res => {
            //1.获取轮播图片
            this.topImages = res.result.itemInfo.topImages
            const data = res.result
            //2.获取商品信息
            this.goods = new Goods(data.itemInfo,data.columns,data.shopInfo.services)
            //3.创建店铺信息的对象
            this.shop = new Shop(data.shopInfo)
        })
    },
    activated(){
        this.$refs.scroll.refresh()
    }
}
</script>
<style scoped>
#detail{
    position:relative;
    z-index:9;
    background-color: #fff;
    height: 100vh;
}
.content{
    height: calc(100% - 44px);
}
.detail-nav{
    position:relative;
    z-index: 9;
    background-color: #fff;
}
</style>