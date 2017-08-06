<template>
  <div class="detail">
    <div class="submit">
      <div class="save">保存</div>
      <div class="cancel">取消</div>
    </div>
    <div class="content">
      <textarea placeholder="任意内容" v-model="msg"></textarea>
    </div>
    <div class="radio">
      <div v-for="item in [1,1,1,1]">
        <i class="iconfont icon-circle1"></i>
        <span>很重要-很紧急</span>
      </div>
    </div>
    <div class="time">
        <i class="iconfont icon-time"></i>
        <span>2017-08-04 13:00</span>
        <i class="iconfont icon-enter"></i>
        <span>2017-08-04 14:00</span>
    </div> 
  </div>
</template>

<script>
export default {
  data(){
    return {
      msg:''
    }
  },
  components:{
  },
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
.radio div{
  float: left;
   margin-right: 10px;
}
.radio span {
  font-size: 16px;
  vertical-align: middle;
}
.radio i {
  font-size: 20px;
  cursor: pointer;
  vertical-align: middle;
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
