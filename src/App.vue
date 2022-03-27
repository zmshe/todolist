<template>
  <div>
    <el-input class="kuan" v-model="input" placeholder="请输入内容"></el-input>
    <el-button type="primary" @click="tianjia">添加</el-button>
    <div>
      <div v-for="item in list" :key="item.id">
        {{item.id+':'+item.value}},
        <el-button type="danger" icon="el-icon-delete" circle size='mini' @click="shanchu(item.id)"></el-button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
    return {
      input: '',
      list:[],
    }
   },
   methods: {
     tianjia(){
       if(this.input==''){
         this.$message.error('错了哦，这是一条错误消息');
         return
      }
      let scx = true;
      for(let i = 0;i<this.list.length;i++){
        if(this.list[i].value==this.input){
          scx=false
        }
      }
      if(scx==false){
        this.$message.error('错了哦，这是一条重复消息');
        return
      }
       this.list.push({id:(Math.random()*10*100).toFixed(0),
      value:this.input,
     });
     this.input="";
     },
     shanchu(v){
       this.list=this.list.filter((item)=>item.id!=v)
     },
     
    },
    
  }
</script>

<style>
.kuan{
  width: 500px;
}
</style>
