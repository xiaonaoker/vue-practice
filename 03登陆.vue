<template>
  <div>
    <div v-show="flag1" id="screen"></div>
    <div id="head_all">
      <div id="head_title">杉杉学习网</div>
      <div id="head_content">
        <span v-show="flag2" class="login" v-on:click="userPage">{{login_user1}}</span><span v-show="flag3" class="login" v-on:click="loginOpen">登陆</span> | <span v-show="flag3" class="register">注册</span><span v-on:click="userExit" v-show="flag2" class="register">退出</span>
      </div>
    </div>
    <div v-show="flag1" class="dialog_login">
      <div class="login_top">
        <div class="login_title">登陆</div><div v-on:click="loginClose" class="login_cross">×</div>
      </div>
      <div class="login_content">
        <div class="login_user">用 户 名 ：<input v-model="login_user1" type="text"></div>
        <div class="login_pass">密 &nbsp&nbsp&nbsp 码 ：<input v-model="login_pass1" type="password"></div>
        <div v-on:click="changeRem" v-bind:class='["rem_count",{"choose_rem":flag4}]'>记住用户名和密码</div>
      </div>
      <div class="login_bottom">
        <div v-on:click="log" class="login_button1">登陆</div>
        <div v-on:click="loginClose" class="login_button2">取消</div>
      </div>
    </div>
  </div>
</template>
<script>
    export default {
      name: "Exercise",
      data(){
        return{
          flag1:false,//登陆框
          flag2:false,//用户|退出
          flag3:true,//登陆|注册
          flag4:false,//记住密码
          login_user1:"",
          login_pass1:"",
        }
      },
      methods:{
        loginOpen(){
          if(this.flag4==false){
            this.login_user1="";
            this.login_pass1="";
          }
          this.flag1=!this.flag1;
        },
        loginClose(){
          this.flag1=!this.flag1;
        },
        log(){
          // user_name=window.localStorage.setItem("user");
          // user_pass=window.localStorage.setItem("pass");
          this.flag1=!this.flag1;
          this.flag2=!this.flag2;
          this.flag3=!this.flag3;

        },
        userPage(){
          alert("这里是"+window.localStorage.getItem("user")+"的个人中心")
        },
        userExit(){
          if(this.flag4==false){
            window.localStorage.clear();
            // window.localStorage.removeItem("");//只忘记密码
          }
          this.flag2=!this.flag2;
          this.flag3=!this.flag3;
        },
        changeRem(){
          this.flag4=!this.flag4;
        }
      },
      watch:{
        login_user1:function(data){
          window.localStorage.setItem("user",data)
        },
        login_pass1:function(data){
          window.localStorage.setItem("pass",data)
        },
      }
    }
</script>
<style scoped>
  *{
    margin:0;
    padding:0;
  }
  #screen{
    z-index:9998;
    background: #000;
    opacity:0.3;
    position:absolute;
    top:0;
    left:0;
    height:100%;
    width:100%;
    /*display:none;*/
  }
  #head_all{
    height:60px;
    width:800px;
    background: lightblue;
    margin:0 auto;
  }
  #head_title{
    float:left;
    display: inline-block;
    font-size: 33px;
    line-height: 61px;
    margin-left:290px;
    letter-spacing:8px;
  }
  #head_content{
    float:right;
    display: inline-block;
    font-size:18px;
    letter-spacing:1px;
    margin:25px 30px;
    color:mediumpurple;
  }
  .login,.register{
    cursor: pointer;
    letter-spacing:2px;
  }
  .dialog_login{
    z-index:9999;
    height:230px;
    width:400px;
    border:0.5px solid #ccc;
    position:absolute;
    top:33%;
    left:33%;
    background:lightyellow;
  }
  .login_top{
    height:38px;
    width:400px;
    background:cornflowerblue;
    display:inline-block;
  }
  .login_title{
    float:left;
    display:inline-block;
    margin-left:30px;
    line-height:38px;
    color:#eee;
    letter-spacing:8px;
    font-size:21px;
  }
  .login_cross{
    float:right;
    display:inline-block;
    height:34px;
    width:36px;
    line-height:34px;
    font-size:30px;
    background:red;
    margin-top:1.5px;
    margin-right:1.5px;
    color:#fff;
    cursor: pointer;
  }
  .login_user{
    display:block;
    /*border:1px solid black;*/
    height:40px;
    width:300px;
    font-size:18px;
    line-height:40px;
    margin:15px auto 0;
  }
  .login_pass{
    display:block;
    /*border:1px solid black;*/
    height:40px;
    width:300px;
    font-size:18px;
    line-height:40px;
    margin:4px 52px 0;
  }
  input{
    height:24px;
    width:150px;
    font-size:16px;
  }
  .rem_count{
    border:1px solid #ccc;
    height:24px;
    width:140px;
    line-height:24px;
    margin:5px auto auto 140px;
    cursor:pointer;
    /*background:#ccc;*/
  }
  .choose_rem{
    background:#fbffb2;
    color:limegreen;
    border:1px solid limegreen;

  }
  .login_button1,.login_button2{
    float:left;
    display: inline-block;
    /*border:1px solid #ccc;*/
    background:#46a0f0;
    color:#fff;
    height:34px;
    width:78px;
    line-height:34px;
    margin:8px 0 auto 115px;
    cursor:pointer;
   }
  .login_button2{
    margin-left:30px;
  }
</style>

