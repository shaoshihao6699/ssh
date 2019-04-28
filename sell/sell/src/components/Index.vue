
<template>
<div class="div2">
    <div class="left">
    <el-aside width="200px" >
    <el-menu :default-openeds="['1', '6']" >
      <el-menu-item >
        <i class="el-icon-menu"></i>
        <span slot="title">首页</span>
      </el-menu-item>
      <el-submenu index="1">
        <template slot="title"><i class="el-icon-document"></i>数据管理</template>
          <el-menu-item index="1-1">用户列表</el-menu-item>
          <el-menu-item index="1-2">商家列表</el-menu-item>
          <el-menu-item index="1-3">食品列表</el-menu-item>
          <el-menu-item index="1-4">订单列表</el-menu-item>
          <el-menu-item index="1-5">管理员列表</el-menu-item>     
      </el-submenu>
      <el-submenu index="2">
        <template slot="title"><i class="el-icon-plus"></i>添加数据</template>
      
          <el-menu-item index="2-1">添加商铺</el-menu-item>
          <el-menu-item index="2-2">添加商品</el-menu-item>
        
      </el-submenu>
      <el-submenu index="3">
        <template slot="title"><i class="el-icon-star-on"></i>图表</template>
          <el-menu-item index="3-1">用户分布</el-menu-item> 
      </el-submenu>
      <el-submenu index="4">
        <template slot="title"><i class="el-icon-edit"></i>编辑</template>
          <el-menu-item index="4-1">文本编辑</el-menu-item> 
      </el-submenu>
      <el-submenu index="5">
        <template slot="title"><i class="el-icon-s-tools"></i>设置</template>
          <el-menu-item index="5-1">管理员设置</el-menu-item> 
      </el-submenu>
      <el-submenu index="6">
        <template slot="title"><i class="el-icon-warning"></i>说明</template>
          <el-menu-item index="6-1">说明</el-menu-item> 
      </el-submenu>
    </el-menu>
  </el-aside>
     </div> 
     <div class="right">
         <div class="login">
           <div>首页</div>
            
            <el-dropdown :hide-on-click="false">
            <div  class="el-dropdown-link img">
            <img src="//elm.cangdu.org/img/default.jpg" alt="">
            </div >
            <el-dropdown-menu slot="dropdown"> 
             <el-dropdown-item>首页</el-dropdown-item>
              <el-dropdown-item>退出</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </div>
         <div class="tu">数据统计</div>
         <div class="tu-1">
            <span class="span1">当日数据：</span>
            <span class="span2">34  新增用户</span>
            <span class="span2">4  新增订单</span>
            <span class="span2">43  新增管理员</span>
         </div>
          <div class="tu-2">
            <span class="span3">总数据：</span>
            <span class="span2">22   注册用户</span>
            <span class="span2">22    订单</span>
            <span class="span2"> 22    管理员</span>
         </div>
       <div id="chartmain" style="width:100%; height: 450px; margin-top:5%"></div>
     </div>
</div>
     
</template>

<script>
import Axios from "axios";
export default {
  data() {
    return {
       
    };
  },
  methods:{
      getUserData() {
       
      }
  },
  mounted(){
      this.on() 
       var timestamp =Date.parse(new Date());
        console.log(timestamp)
  },
   methods: {
      on(){
          let aaa= this.$echarts.init(document.getElementById("chartmain"))
          aaa.setOption({
               title: {
        text: '走势图',
    },
    tooltip: {
        trigger: 'axis'
    },
    legend: {
        data:['新注册用户','新增订单','新增管理员']
    },
    toolbox: {
        show: true,
        feature: {
            dataZoom: {
                yAxisIndex: 'none'
            },
            dataView: {readOnly: false},
            magicType: {type: ['line', 'bar']},
            restore: {},
            saveAsImage: {}
        }
    },
    xAxis:  {
        type: 'category',
        boundaryGap: false,
        data: ['2019-04-22','2019-04-23','2019-04-24','2019-04-25','2019-04-26','2019-04-27','2019-04-28']
    },
    yAxis: {
        type: 'value',
         min: 0,
            max: 200,
            interval: 50,
        axisLabel: {
            formatter: '{value}'
        }
    },
    series: [
        {
            name:'新注册用户',
            type:'line',
            data:[199, 113, 77, 50, 38, 13, 0,5],
            markPoint: {
                data: [
                    {type: 'max', name: '最大值'},
                    {type: 'min', name: '最小值'}
                ]
            },
        },
        {
            name:'新增订单',
            type:'line',
            data:[15, 3, 2, 30, 3, 21, 2,17],
            markPoint: {
                 data: [
                    {type: 'max', name: '最大值'},
                    {type: 'min', name: '最小值'}
                ]
            },
        },
        {
            name:'新增管理员',
            type:'line',
            data:[124, 129, 123, 124,127, 13, 22],
            markPoint: {
                 data: [
                    {type: 'max', name: '最大值'},
                    {type: 'min', name: '最小值'}
                ]
            },
        },
    ]
          })
      },
      
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >
*{
  margin: 0;
  padding: 0;
  list-style: none;  
  box-sizing:border-box;
}
 .div2{
   width: 100%;
   display: flex;
 }
 .left{
   width: 15%;   
 }
 .right{
   width: 85%;   
 }
 .login{
   padding-left: 30px;
   padding-right: 30px;
   width: 100%;
   background:#EFF2F7;
   height: 50px;
   line-height: 50px;
   color: #97B8DC;
   font-size: 13px;
   display: flex;
   justify-content:space-between;
 }
 .img{
   width: 50px;
   height: 50px;
   border-radius: 50%;
 }
 img{
   width: 100%;
   height: 100%;
   border-radius: 50%;
 }
 .tu{
   margin-top: 10px;
   width: 100%;
   text-align: center;
   font-size: 30px;
 }
 span{
   margin-top: 10px;
   display: inline-block;
   width: 150px;
   height: 30px;
   text-align: center;
   line-height:30px; 
   margin-left: 20px;
   border-radius: 5px;
 }
 .span1{
   background: #FF9800;
 }
  .span3{
   background: #20A0FF;
 }
 .span2{
    background: #E5E9F2;
 }
</style>
