<template>
<div>   
    <tab-bar>
      <tab-bar-item path="/home" activeColor="blue">
        <img slot="tabbar-img" src="../../../assets/img/tabbar/home.svg">
        <img slot="active-tabbar-img" src="../../../assets/img/tabbar/home_active.svg">
        <div slot="tabbar-txt">首页</div>
      </tab-bar-item>
      <tab-bar-item path="/category">
        <img slot="tabbar-img" src="../../../assets/img/tabbar/category.svg">
        <img slot="active-tabbar-img" src="../../../assets/img/tabbar/category_active.svg">
        <div slot="tabbar-txt">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/cart">
        <img slot="tabbar-img" src="../../../assets/img/tabbar/shopcart.svg">
        <img slot="active-tabbar-img" src="../../../assets/img/tabbar/shopcart_active.svg">
        <div slot="tabbar-txt">购物车</div>
      </tab-bar-item>
      <tab-bar-item path="/me">
        <img slot="tabbar-img" src="../../../assets/img/tabbar/profile.svg">
        <img slot="active-tabbar-img" src="../../../assets/img/tabbar/profile_active.svg">
        <div slot="tabbar-txt">我的</div>
      </tab-bar-item>
    </tab-bar>
</div>
</template>

<script>
import TabBar from "../../common/tabbar/TabBar1.vue"
import TabBarItem from "../../common/tabbar/TabBarItem.vue"
export default {
    name:'MainTabBar',
    components:{
        TabBar,TabBarItem
    }
}
</script>
<style scoped>
/* @import url(); 引入css类 */

</style>