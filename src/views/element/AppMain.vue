<template>
  <div>
      <p class="input-wrapper">  
        <input v-model="input" placeholder="请输入内容" type="text" class="my-input" @keyup.enter="addmessage">  
        <el-button type="primary" @click="addmessage" plain>添加</el-button>
      </p>
    <el-table
    :data="tableData"
    stripe
    style="width: 100% "
    height="600px"
    size="mini"
    >
    <el-table-column
      prop=""
      label=""
      width="200">
    </el-table-column>
    <el-table-column
      prop="id"
      label="id"
      width="400">
    </el-table-column>
    <el-table-column
      prop="message"
      label="消息"
      width="500"
      >
    </el-table-column>
    <el-table-column
      prop="time"
      label="时间">
    </el-table-column>
    <el-table-column
      fixed="right"
      label="操作"
      width="150">
      <template slot-scope="scope">
        <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
        <el-button type="text" size="small" @click="emite(scope.row)">编辑</el-button>
        <el-button type="text" size="small" @click="delete_row(scope.row)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>
  <el-dialog
      title="请输入内容"
      :visible.sync="dialogVisible"
      :close-on-click-modal="false"
      @opened="focusInput"
    >
      <el-input ref="inputRef" v-model="inputValue" placeholder="请输入内容" @keyup.enter.native="confirmInput"></el-input>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取消</el-button>
        <el-button type="primary" @click="confirmInput" >确定</el-button>
      </div>
    </el-dialog>

  </div>
    
  
</template>
<script>
import { Alert } from 'element-ui';

var current_row=''

export default {
    data() {
    return {
      input: '',
      tableData:JSON.parse(localStorage.getItem('myData'))||[],
      dialogVisible:false,
      inputValue:'',
      ids:0
    }
  },
  methods: {
      handleClick(row) {
        this.$alert(row.message)
      },
      addmessage(){
        this.tableData.push({id:this.ids+1,message:this.input,time:new Date().toLocaleString()})
        this.ids=this.ids+1
      },
      emite(row){
        this.dialogVisible = true;
        current_row=row
      },
      confirmInput(){
        current_row.message=this.inputValue;
        this.dialogVisible = false
      },
      focusInput(){
        this.$refs.inputRef.$el.querySelector('input').focus();
      },
      delete_row(row){
        const index=this.tableData.indexOf(row);
        this.tableData.splice(index, 1);
      },
      
    },
    watch:{
      tableData:{
        deep:true,
        handler(){
          localStorage.setItem('myData',JSON.stringify(this.tableData));
        }
      }
      
      //this.tableData=localStorage.getItem('myData');
    }
}
</script>
<style>
.input-wrapper {  
  display: flex;  
  justify-content: center;  
  align-items: center;  
  height: 10vh; /* 仅用于示例，使输入框垂直居中 */  
}  
  
.my-input {  
  width: 300px; /* 设置输入框宽度 */  
  padding: 10px; /* 设置内边距 */  
  border: none; /* 移除边框 */  
  border-radius: 5px; /* 设置边框圆角 */  
  background-color: #f0f0f0; /* 设置背景颜色 */  
  font-size: 16px; /* 设置字体大小 */  
  color: #333; /* 设置字体颜色 */  
}  
  
/* 添加一些悬停效果 */  
.my-input:hover {  
  background-color: #e0e0e0;  
}  
  
/* 添加一些焦点效果 */  
.my-input:focus {  
  outline: none; /* 移除默认的焦点轮廓 */  
  box-shadow: 0 0 5px rgba(81, 203, 238, 1); /* 添加一些阴影效果 */  
}
</style>