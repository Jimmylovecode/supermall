<template>
<div class="tabbar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="tabbar-img"></slot></div>
    <div v-else><slot name="active-tabbar-img"></slot></div>
    <div :style="activeStyle"><slot name="tabbar-txt"></slot></div>
    
</div>
</template>

<script>
export default {
    data(){
        return{
            /* isActive:true */
        }
    },
    computed:{
        isActive(){
            return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle(){
            return this.isActive ? {color:this.activeColor} : {}
        }
    }
    ,
    props:{
        path:String,
        activeColor:{
            type:String,
            default:'red'
        }
    },
    methods:{
        itemClick(){
            this.$router.replace(this.path).catch(err => err)
        }
    }
}
</script>
<style scoped>
.tabbar-item{
    flex:1;
    text-align: center;
    height: 49px;
    font-size: 14px;
}
.tabbar-item img{
    width: 24px;
    height: 24px;
    margin-top:3px;
    vertical-align: middle;
}

</style>