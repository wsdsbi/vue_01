

<template>
  <div id="app">
    <el-container>
  <el-header>
    <p>小韩阿什顿记事本</p>
  </el-header>
  <el-main>
    <app-main >></app-main>
  </el-main>
</el-container>
  </div>
</template>

<script>
import HelloWorlds from './views/element/HelloWorlds.vue'
import AppMain from './views/element/AppMain.vue'
export default {
  components: { HelloWorlds,AppMain },
  data(){
    return{
      message:'123',
      id:'',
      message:''
    }
  },
  methods:{
    look(id){

        '<div>{{id}}</div>'
    }
  }
}
</script>
<style>
.el-header, .el-footer {
  background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    color: #130707;
    background-color: #f6f7f8;
    text-align: center;
    line-height: 160px;
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>