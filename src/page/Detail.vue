<template>
  <div class="detail">
    <div class="submit">
      <div class="save" @click="save">保存</div>
      <div class="cancel" @click="cancel">取消</div>
    </div>
    <div class="content">
      <textarea placeholder="任意内容" v-model="msg"></textarea>
    </div>
    <div class="radio">
      <div class="selection" v-for="item in itemData">
        <i class="iconfont icon-circle1" :style="{color: item.color}" @click="selectItem(item)"></i>
        <i class="iconfont icon-circle" :style="{color: item.color}" v-show="item.selected"></i>
        <span>{{item.selected?item.title:""}}</span>
      </div>
    </div>
    <div class="time">
        <i class="iconfont icon-time"></i>
        <span>{{startTime}}</span>
        <i class="iconfont icon-enter"></i>
        <span>{{endTime}}</span>

    </div> 
  </div>
</template>

<script>
export default {
  data(){
    return {
      itemData:[{
        title: "很重要-很要紧",
        color: "#EF6A34",
        id:1,
        selected: false
      },{
        title: "重要-不要紧",
        color: "#F6B55A",
        id:2,
        selected: false
      },{
        title: "不重要-紧急",
        color: "#1DAFED",
        id:3,
        selected: false
      },{
        title: "不重要-不紧急",
        color: "#90C744",
        id:4,
        selected: false
      }],
      msg:'',
      selectId: 1,
      startTime:'2017-08-04 14:00',
      endTime:"2017-08-16 15:00"
    }
  },
  components:{
  },
  methods:{
    selectItem: function(item){
      this.itemData.map(data=>{
        data.selected = false;  
        return data;
      });
      item.selected = true;
      this.selectId = item.id;
    },
    cancel:function(){
      this.$router.go(-1);
    },
    save:function(){
      if(!this.msg || !this.endTime){
        return false;
      }

      var _saveData = JSON.parse(localStorage.getItem('saveData')) || [];
      _saveData.push({msg: this.msg, endTime: this.endTime, id: this.selectId});
    
      localStorage.setItem("saveData",JSON.stringify(_saveData));
      this.$router.go(-1);
    }
  },
  mounted:function(){
    this.itemData.map(item=>{
      if(item.id == this.$route.query.id){
        item.selected = true;
        this.selectId = item.id;
      }
      return item;
    })
     
  }
}
</script>

<style scoped>
.submit{
  width: 100%;
  height: 50px;
  line-height: 50px;
  font-size: 20px;
}
.submit div{
  float: right;
  width: 50px;
  cursor: pointer;
}
.save {
  color: #47D2F3;
}
.content textarea{
  width: 100%;
  height: 200px;
  background-color: #FFEDE7;
  border: 0 none;
  outline:none;
  padding: 10px 20px;
  box-sizing: border-box;
  resize:none;
  font-size: 16px;
  border-bottom: 1px solid #ccc;
}
.radio {
  width: 100%;
  height: 50px;
  line-height: 50px;
  padding: 0 20px;
  border-bottom: 1px solid #ccc;
  overflow: hidden;
}
.radio .selection{
  position: relative;
  float: left;
   margin-right: 10px;
}
.selection i{
  position: absolute;
  font-size: 20px;
  cursor: pointer;
}
.selection span {
  font-size: 16px;
  margin-left: 30px;
}

.time {
  width: 100%;
  height: 50px;
  line-height: 50px;
  padding: 0 20px;
  border-bottom: 1px solid #ccc;
}
.time span {
  font-size: 16px;
  vertical-align: middle;
}
.time i {
  font-size: 20px;
  vertical-align: middle;
}
</style>
