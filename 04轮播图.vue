<template>
  <div>

    <div class="screen">
      <div v-show="flag1" class="picture1"></div>
      <div v-show="flag2" class="picture2"></div>
      <div v-show="flag3" class="picture3"></div>

      <div v-on:click="goLeft" class="left"><</div>
      <div v-on:click="goRight" class="right">></div>

      <span v-on:click="choose1" v-bind:class='["point1",{"point":flag==1}]'></span>
      <span v-on:click="choose2" v-bind:class='["point2",{"point":flag==2}]'></span>
      <span v-on:click="choose3" v-bind:class='["point3",{"point":flag==3}]'></span>
    </div>

    <br>
    <br>
  </div>
</template>
<script>
    export default {
      name: "Exercise",
      data(){
        return{
          flag1:true,//第一张图
          flag2:false,//第二张图
          flag3:false,//第三张图
          flag:1,//表示展示的是第几张图
        }
      },
      methods:{
        choose1(){
          this.flag=1;
          this.flag1=true;
          this.flag2=false;
          this.flag3=false;
        },
        choose2(){
          this.flag=2;
          this.flag1=false;
          this.flag2=true;
          this.flag3=false;
        },
        choose3(){
          this.flag=3;
          this.flag1=false;
          this.flag2=false;
          this.flag3=true;
        },
        goLeft(){
          if(this.flag==1){
            this.flag=3;
            this.flag1=false;
            this.flag2=false;
            this.flag3=true;

          }
          else if(this.flag==2){
            this.flag=1;
            this.flag1=true;
            this.flag2=false;
            this.flag3=false;
          }
          else if(this.flag==3){
            this.flag=2;
            this.flag1=false;
            this.flag2=true;
            this.flag3=false;
          }
        },
        goRight(){
          if(this.flag==1){
            this.flag=2;
            this.flag1=false;
            this.flag2=true;
            this.flag3=false;
          }
          else if(this.flag==2){
            this.flag=3;
            this.flag1=false;
            this.flag2=false;
            this.flag3=true;
          }
          else if(this.flag==3){
            this.flag=1;
            this.flag1=true;
            this.flag2=false;
            this.flag3=false;
          }
        },
        auto(){
          var that=this;
          setInterval(function(){
            that.goRight();
          },1300)
        },
      },
      watch:{},
      created(){
        this.auto();
      },
    }
</script>
<style scoped>
  *{
    margin:0;
    padding:0;
  }
  .screen{
    height:430px;
    width:800px;
    border:30px solid #dde6f8;
    border-radius:20px;
    margin:auto;
  }
  .picture1,.picture2,.picture3{
    float:left;
    display: inline-block;
    height:400px;
    width:800px;
    background-image: url("img/01.png");
  }
  .left,.right{
    display: inline-block;
    font-size:60px;
    font-weight: bolder;
    color:yellow;
    margin-top:-230px;
    cursor: pointer;
  }
  .left{
    float:left;
    margin-left:25px;
  }
  .right{
    float:right;
    margin-right:25px;
  }
  .point1,.point2,.point3{
    float:left;
    display:inline-block;
    height:20px;
    width:20px;
    border-radius:20px;
    border:1px solid #bbb;
    margin-right:30px;
    margin-top:-12px;
    cursor: pointer;
    background: #ffe4df;
  }
  .point1{
    margin-left:340px;
  }
  .point{
    background:lightpink;
  }
  .picture2{
    /*display:none;*/
    background-image: url("img/02.png");
  }
  .picture3{
    /*display:none;*/
    background-image: url("img/03.png");
  }





  /*.picture1{*/
    /*height:400px;*/
    /*width:800px;*/
    /*border:1px solid #ccc;*/
    /*background-image: url("img/01.png");*/
    /*margin:auto;*/
  /*}*/
  /*.picture2{*/
    /*height:400px;*/
    /*width:800px;*/
    /*border:1px solid #ccc;*/
    /*background-image: url("img/02.png") ;*/
    /*margin:auto;*/
  /*}*/
  /*.picture3{*/
    /*height:400px;*/
    /*width:800px;*/
    /*border:1px solid #ccc;*/
    /*background-image: url("img/03.png") ;*/
    /*margin:auto;*/
  /*}*/

</style>

