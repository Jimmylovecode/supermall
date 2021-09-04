<template>
    <swiper class="change">
        <swiper-item  v-for="(item,index) in imageSwiper" :key="index">
            <img :src="item" alt="">
        </swiper-item>
    </swiper>
</template>

<script>
import {Swiper,SwiperItem} from '../../../components/common/swiper/index'
export default {
  components: { Swiper,SwiperItem },
  props:{
      imageSwiper:{
          type:Array
      }
  }
}
</script>
<style scoped>
.change{
    height: 300px;
    overflow: hidden;
}

</style>