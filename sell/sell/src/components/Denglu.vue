<template>
  <div id="app">
      <p>elm后台管理系统</p>
      <div class="box" style=" box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)">
        
        <div >
          <div class="inp">
            <el-input v-model="name" placeholder="请输入内容" ></el-input>
          </div >
          <div class="inp">
            <el-input placeholder="请输入密码" v-model="age" show-password ></el-input>
          </div>
            <el-button type="primary" @click="denglu">登陆</el-button>
        </div>
        <div>

        </div>
    </div>    
  </div>
</template>

<script>
export default {
  name: 'Denglu',
  data(){
    return {
        name:'',
        age:'',
        userinfo:{}
    }
 },
methods:{
      denglu(){ 
        let data={
             user_name:this.name,
             password:this.age
         } 
        this.$axios.post(`https://elm.cangdu.org/admin/login`,data)
        .then(res => {
           if(res.data.status=1){
               this.$router.push({path:'/index'})
           }else if(res.data.status===0){
             alert(res.data.message)
           }
        })
      }   
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
body{
  background:#324057 ;
}
#app {
  width: 100%;
  height: 100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
p{
margin-top: 10%;
color: bisque;
font-weight: 400;
font-size: 30px;

}
.box{
  margin-top: 3%;
  background: beige;
  height: 250px;
  width:40%;
  margin-left: 30%;
  border-radius: 10px; 
  
}
button{
  background: beige;
}
.inp{
  line-height: 60px;
  margin-left:10%; 
  width: 80%;
  height: 60px;
}
</style>
