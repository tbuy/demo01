<template>
  <div id="app">
    <div class="item-box" v-for="(item,index) in itemData">
      <v-item :itemData="item" :index="index"></v-item>
    </div>
  </div>
</template>

<script>
import Item from './components/Item.vue'
export default {
  data(){
    return {
      itemData:[{
        title: "很重要-很要紧",
        bg: "#FFEDE7",
        color: "#EF6A34"
      },{
        title: "重要-不要紧",
        bg: "#FFEFCB",
        color: "#F6B55A"
      },{
        title: "不重要-紧急",
        bg: "#D6F4FE",
        color: "#1DAFED"
      },{
        title: "不重要-不紧急",
        bg: "#EEFFDD",
        color: "#90C744"
      }]
    }
  },
  components:{
    'v-item': Item
  },
}
</script>

<style scoped>

  .item-box{
    float: left;
    width: 50%;
    height: 300px;
    padding: 10px;
    border-top: 1px solid #ccc;
    border-left: 1px solid #ccc;
    box-sizing: border-box;
  }
  .item-box:nth-child(1),
  .item-box:nth-child(2){
    border-top: 0 none;
  }
   .item-box:nth-child(1),
  .item-box:nth-child(3){
    border-left: 0 none;
  }
</style>
