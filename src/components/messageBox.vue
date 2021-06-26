<template>
  <div :class="'box '+transparent">
        <button @click="openWindow">点击打开窗口</button>
        <div v-if="visible" class="window">
          <div class="closewindow" @click="closeWindow">X</div>
        </div>
<!--    <div v-if="visible" class="window"></div>-->
  </div>
</template>

<script>
export default {
  name: "messageBox",
  data(){
    return{
      transparent:'unparent',
      visible:false
    }
  },
  methods: {
    openWindow() {
      if (this.transparent === 'unparent') {
        this.transparent = 'parent'
        this.visible = true
      }

    },
    closeWindow(){
      this.transparent = 'unparent'
      this.visible = !this.visible
    }
  }
}
</script>

<style scoped>
  .box{
    position: fixed;
    top: 0px;
    left: 0px;
    /*将box设置为满屏*/
    width: 100vw;
    height: 100vh;
  }
  .parent{
    background: rgba(200,200,200,0.5);
  }
  .unparent{
    background: rgba(200,200,200,1);
  }
  .button{
    height: 100px;
    width: 200px;
    margin-top: 100px;
    background: red;
  }
  .window{
    width: 400px;
    height: 200px;
    position: absolute;
    background: white;
    border-radius: 20px;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
  }
  .closewindow{
    width: 20px;
    height: 20px;
    border-radius: 10px;
    background: #42b983;
    position: relative;
    left: 370px;
    top: 10px;
    text-align: center;
  }
</style>