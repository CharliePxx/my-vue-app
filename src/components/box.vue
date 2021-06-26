<template>
  <div class="box">
    {{msgA}}
    <button @click="onClick()">点我</button>
  </div>
</template>

<script>
export default {
  name: "box",
  data(){
    return{
      msgFromChild:'hello father'
    }
  },
  props:{
    msgA: String,
    callback:Function
  },
  methods:{
    onClick(){
      this.$emit('my-func',1,2,3,4);
    }
  },
  mounted() {
    this.callback(this.msgFromChild)
  }
}
</script>

<style scoped>
  /*.box{*/
  /*  height: 100px;*/
  /*  width: 100px;*/
  /*  background: #42b983;*/
  /*}*/
</style>