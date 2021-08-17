<template>
<div class="good-list">
   <goods-list-item v-for="(item,index) in goods" :key="index" :goods-item="item"/>
</div>
</template>

<script>
import GoodsListItem from "./GoodsListItem.vue"
export default {
    props:{
        goods:{
            type:Array,
            default(){
                return []
            }
        }
    },
    components:{
        GoodsListItem
    }
}
</script>
<style scoped>
.good-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    background-color: var(--color-background);

    padding: 2px;
  }

</style>