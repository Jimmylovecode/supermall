<template>
<swiper>
  <swiper-item v-for="(item,index) in banners" :key="index">
    <a :href="item.link">
      <img :src="item.image">
    </a>
  </swiper-item>
</swiper>
</template>

<script>
import {Swiper,SwiperItem} from '../../../components/common/swiper/index'
export default {
    props:{
        banners:{
            type:Array,
            default(){
                return []
            }
        }
    },
    components:{
        SwiperItem,
        Swiper
    }
}
</script>
<style scoped>
/* @import url(); 引入css类 */

</style>