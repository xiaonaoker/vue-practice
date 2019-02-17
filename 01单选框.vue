<template>
  <div>
    <div id="all">
      <div class="title">1.杉杉的生日是哪一天？</div>
      <div class="content">
        <div v-on:click="chooseOne(1)" v-bind:class='["chooseAC",{"state":numbering==1}]'>A.2月2日</div>
        <div v-on:click="chooseOne(2)" v-bind:class='["chooseBD",{"state":numbering==2}]'>B.3月10日</div>
        <div v-on:click="chooseOne(3)" v-bind:class='["chooseAC",{"state":numbering==3}]'>C.6月9日</div>
        <div v-on:click="chooseOne(4)" v-bind:class='["chooseBD",{"state":numbering==4}]'>D.6月14日</div>
      </div>
      <div v-on:click="judge" class="button">提交</div>
    </div>
  </div>
</template>
<script>
    export default {
        name: "Exercise",
        data(){
          return{
          numbering:0,
        }
      },
      methods:{
        chooseOne(n){
          this.numbering=n;
        },
        judge(){
          if(this.numbering==2){
            alert("答案正确");
          }else if(this.numbering==1||this.numbering==3||this.numbering==4){
            alert("答案错误")
          }else if(this.numbering==0){
            alert("您还未选择")
          }

        }
      }
    }
</script>
<style scoped>
  #all{
    height:300px;
    width:600px;
    background:cornflowerblue;
    margin:0 auto;
  }
  .title{
    color:#fff;
    float:left;
    margin-left:68px;
    margin-top:34px;
    font-size:30px;
  }
  .content{
    float:left;
    height:150px;
    width:500px;
    margin-left:50px;
  }
  .chooseAC{
    float:left;
    height:50px;
    width:200px;
    color:#eee;
    font-size:24px;
    line-height:49px;
    text-align:center;
    cursor:pointer;
    margin-top:19px;
    margin-left:32px;
    border-radius:8px;
    background:royalblue;
    border:1px solid royalblue;
  }
  .chooseBD{
    float:left;
    height:50px;
    width:200px;
    /*border:1px solid blue;*/
    color:#eee;
    font-size:26px;
    line-height:49px;
    text-align:center;
    cursor:pointer;
    margin-top:19px;
    margin-left:32px;
    border-radius:8px;
    background:royalblue;
    border:1px solid royalblue;
  }
  .state{
    background:#fbffb2;
    color:limegreen;
    border:1px solid limegreen;
  }
  .button{
    float:left;
    height:41px;
    width:90px;
    background: #eee;
    color:blue;
    font-size:26px;
    line-height:40px;
    text-align:center;
    border-radius: 6px;
    margin:12px 255px;
    cursor:pointer;
  }
</style>
