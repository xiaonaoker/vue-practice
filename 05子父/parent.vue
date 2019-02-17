<template>
  <div>
    父亲
    <input type="text" v-model="lifemsg">
    <Son :title="msg" :lifemsg="lifemsg" :num="num" :objdata="myobj" @sendmsg="getMsg"/>
    <button @click="changeMsg">按钮</button>
    {{info}}
  </div>
</template>
<script>
  import Son from"./son"
  export default {
    components:{//把子组件绑定进去
      Son,
    },
    name: "parent",
    data(){
      return{
        msg:"我是活的数据",
        lifemsg:"hello",
        num:10,
        myobj:{
          name:"naoker",
          age:21,
        },

        info:"",
      }
    },
    methods:{
      changeMsg(event){
        this.msg="我是修改后的数据";
      },
      getMsg(data){
        // console.log(data);
        this.info=data;
      },
    },
    watch:{},
    created(){},
  }
</script>
<style scoped>/*表示局部*/
  *{
    margin:0;
    padding:0;
  }
</style>
