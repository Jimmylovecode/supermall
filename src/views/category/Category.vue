<template>
<div class="wrapper">
<ul class="content">
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
  <li>nihao</li>
</ul>
</div>
</template>

<script>
import BScroll from 'better-scroll'
    export default {
      name: "Category",
      mounted(){
        this.scroll = new BScroll(document.querySelector('.wrapper'),{
          probeType:3,
          pullUpLoad:true
        })
       /*  this.scroll.on('scroll',(position) => {
          console.log(position)
        }) */
        this.scroll.on('pullingUp', () => {
          console.log('上拉加载更多');
          
        })
      }
    }
</script>

<style scoped>
.wrapper{
  height: 150px;
  background-color: red;
}
</style>
