<template>
<div>
  儿子
  {{title}}-{{lifemsg}}-{{num*2}}-{{objdata.name}}<!--父到子-->
  <button @click="sendMsg">子到父</button>
</div>
</template>

<script>
    export default {
      // props:["title","lifemsg","num"],//子接受父传来的数据
      props:{
        title:[String,Number],
        lifemsg:{
          type:String,
          required:true,
        },
        num:{
          type:Number,
          default:5,
        },
        objdata:{
          type:Object,
          default:function(){
            return{
              name:"未知",
              age:0,
            }
          },
        }
      },
      name: "son",
      data(){
        return{
          msg:"我是子组件数据",
        }
      },
      methods:{
        sendMsg(event){//两个参数(1)key(2)数据
          this.$emit("sendmsg",this.msg)
        }
      }
    }
</script>

<style scoped>

</style>
