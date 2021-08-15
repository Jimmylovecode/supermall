<template>
<div class="recommend">
    <div v-for="(item,index) in recommends" :key="index" class="recommend-item">
        <a :href="item.link">
        <img :src="item.image" alt="">
        <div>{{item.title}}</div>
        </a>
    </div>
</div>
</template>

<script>
export default {
    props:{
        recommends:{
            type:Array,
            default(){

            }
        }
    }
}
</script>
<style scoped>
/* @import url(); 引入css类 */
.recommend{
    display: flex;
    text-align: center;
    font-size: 12px;
    padding:15px 0 30px;
    border-bottom: 10px solid #eee;
}
.recommend-item{
    flex:1
}
.recommend-item img{
    width:80%;
    margin-bottom: 6px;
}
</style>