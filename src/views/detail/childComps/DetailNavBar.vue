<template>
<div>
    <nav-bar>
        <div slot="left" class="back" @click="backClick">
            <img src="../../../assets/img/common/back.svg" alt="">
        </div>
        <div slot="center"  class="title">
        <div v-for="(item,index) in title" 
        :key="index" class="title-item" :class="{active: index === currentIndex}"
        @click="titleClick(index)">
        {{item}}
        </div>
        </div>
     </nav-bar>
</div>
</template>

<script>
import NavBar from '../../../components/common/navbar/NavBar.vue'
export default {
    components: {
        NavBar 
        },
    data(){
        return {
            title:['商品','参数','评论','推荐'],
            currentIndex:0
        }
    },
    methods:{
        titleClick(index){
            this.currentIndex = index
        },
        backClick(){
            this.$router.back(-1)
        }
    }

}
</script>
<style scoped>
.title{
    display: flex;
}
.title-item{
    flex:1;
    font-size: 14px;
}
.active{
    color:var(--color-high-text)
}
.back{
    margin-top:6px
}

</style>