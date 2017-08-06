<template>
  <div class="item">
    <div class="title" :style="{backgroundColor:item.bg}">
      <span :style="{color: item.color}">{{item.title}}</span>
      <i class="iconfont icon-add" @click="add(index)"></i>
    </div>
    <div class="content" v-for="i in [1,1,1,1]">
      <i class="iconfont icon-circle1" :style="{color: item.color}"></i>
      <span>完成</span>
      <span class="time">08/03 10:00</span>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    item:{
      type: Object,
      default: function(){
        return {}
      }
    },
    index:{
      type:Number,
      default: 0
    }
  },
  data () {
    return {
    }
  },
  methods:{
    add: function(index){
      console.log(index)
       this.$router.push('/detail');
    }
  }
}
</script>

<style scoped>
  .title{
    height: 50px;
    line-height: 50px;
    padding: 0 10px;
    box-sizing: border-box;
    width: 100%;
  }
  .title span{
    font-size: 20px;
    color:red;
    vertical-align: middle;
  }
  .title i{
    font-size: 20px!important;
    vertical-align: middle;
    color: #999;
    float: right;
  }
  .content {
    font-size: 16px;
    height: 40px;
    line-height: 40px;
    padding: 0 10px;
    box-sizing: border-box;
    border-bottom: 1px dashed #ccc;
  }
  .content i {
    font-size: 24px;
    margin-left: 10px;
    vertical-align: middle;
  }
  .content span{
    vertical-align: middle;
  }
  .content .time{
    float: right;
    color: red;
    margin-right: 10px;
  }
</style>
