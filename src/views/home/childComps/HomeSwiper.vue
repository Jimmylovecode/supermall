<template>
<swiper>
  <swiper-item v-for="(item,index) in banners" :key="index">
    <a :href="item.link">
      <img :src="item.image" @load="imageLoad">
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
    },
    data(){
      return {
        isLoad:false
      }
    },
    methods:{
      imageLoad(){
        if(!this.isLoad){
          this.$emit('imageLoad')
          this.isLoad = true
        }
      }
    }
}
</script>
<style scoped>
/* @import url(); 引入css类 */

</style>