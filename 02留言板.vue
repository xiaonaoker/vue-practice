<template>
  <div>
    <div id="write">
      <h1>留言板</h1>
      <textarea v-model="words" v-on:keyup="count1" class="ipt" placeholder="请输入您的留言！"></textarea>
      <div id="number1"><span id="count1">{{words.length}}</span> /70</div>
      <div id="sub" v-on:click="submit">提交</div>
    </div>

    <div id="show_area">
      <h1>已发布的留言</h1>
      <div id="number2">总计<span id="count2">{{items.length}}</span>条评论</div>
      <ul>
        <li v-for="item in items" class="show_board">{{item}}</li>
      </ul>

    </div>

  </div>
</template>
<script>
    export default {
        name: "Exercise",
        data(){
          return{
            words:"",
            num1:0,
            message1:"",
            items:[],
        }
      },
      methods:{
        count1(){
          this.num1=this.num1+1;
        },
        submit(){
            this.message1=this.words;
            this.items.push(this.words);
            this.words="";

        }
      },
      watch:{
        words:function(data){
          if(this.words.length<=70){
            this.words=data;
          }else{
            alert("长度超出");
          this.words=this.words.substring(0,70);
          }
        }
      }
    }
</script>
<style scoped>
  *{
    margin:0;
    padding:0;
  }
  #write{
    border:1px solid #ccc;
    height:240px;
    width:800px;
    background: #ffeed7;
  }
  h1{
    margin:10px auto 0;
  }
  .ipt{
    resize:none;
    color:#666;
    height:100px;
    width:600px;
    background: #feffe1;
    line-height:30px;
    font-size:23px;
    text-indent:10px;
    letter-spacing:1.1px;
    display:block;
    margin:10px 100px;
  }
  #number1{
    float: right;
    display:inline-block;
    height:38px;
    width:78px;
    line-height:38px;
    text-align: center;
    font-size:22px;
    /*overflow: hidden;*/
    color:green;
    letter-spacing:1.2px;
    margin-right:102px;
    margin-top:-48px;
  }
  #sub{
    height:40px;
    width:78px;
    line-height:38px;
    text-align: center;
    background-color:cornflowerblue;
    font-size:22px;
    /*overflow: hidden;*/
    color:#eee;
    cursor: pointer;
    margin-top:14px;
    margin-left:625px;
  }


  #show_area{
    min-height:400px;
    width:800px;
    border:1px solid #ccc;
    margin-top:5px;
    background:#f1f1f1;
  }
  .show_board{
    min-height:28px;
    height:auto;
    width:600px;
    border:1px solid #ccc;
    margin:10px auto 5px 10px;
    color:#666;
    letter-spacing:2px;
    text-indent:20px;
    display:inline-block;
    font-family:宋体;
    font-size: 23px;
    font-weight:bold;
    background: #feffe1;
    /*vertical-align: bottom;*/
    padding:5px;
    text-align:left;
  }
  #number2{
    height:20px;
    width:120px;
    float:right;
    font-size:18px;
    margin:-24px 50px auto auto;
  }
  #count2{
    color:orange;
  }
</style>
