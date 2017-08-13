<template>
  <div class="item">
    <div class="title" :style="{backgroundColor:item.bg}">
      <span :style="{color: item.color}">{{item.title}}</span>
      <i class="iconfont icon-add" @click="add(item.id)"></i>
    </div>
    <div class="wrap">
      <div class="content" v-for="i in listData">
        <i class="iconfont icon-circle1" :style="{color: item.color}"></i>
        <span class="msg">{{i.msg}}</span>
        <span class="time">{{i.endTime | time}}</span>
      </div>
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
      listData:[],
    }
  },
  filters:{
    time:function(value){
      return value.slice(5,16);
    }
  },
  methods:{
    add: function(id){
       this.$router.push({path: '/detail',query:{id:id}});
    }
  },
  mounted: function(){
    var _listData = JSON.parse(localStorage.getItem('saveData'))||[];
    _listData.forEach(value=>{
      if(value.id == this.item.id){
        this.listData.push(value);
      }
    })
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
  .wrap{
    height: 240px;
    overflow-y: auto;
    overflow-x: hidden;
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
    .content .msg{
    display: inline-block;
    width: 50%;
    overflow: hidden;
    text-overflow: ellipsis;
  }
</style>
