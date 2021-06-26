<template>
  <div :class="'btn '+btnColor" @click="changeButton">
    <div :class="'round '+roundPosition">

    </div>
  </div>
</template>

<script>
export default {
name: "switchButton",
  data(){
    return{
      roundPosition:'roundLeft',
      btnColor:'grey'
    };
  },
  methods:{
    changeButton(){
      if (this.roundPosition === 'roundLeft' ){
        this.roundPosition = 'roundRight'
        this.btnColor = 'green'
      }else{
        this.roundPosition = 'roundLeft'
        this.btnColor = 'grey'
      }
    }
  },
}
</script>

<style scoped>
  .btn{
    width: 500px;
    height: 200px;
    /*background: darkgray;*/
    border-radius: 100px;
    border: 1px solid black;
    position: absolute;
  }
  .grey{
    background: darkgray;
  }
  .green{
    background: #8ee316;
  }
  .round{
    position: relative;
    width: 180px;
    height: 180px;
    background: white;
    border-radius: 90px;
    transition: 1s ease;
    animation: abc 1s infinite;
  }
  @keyframes abc {
    0%{left:10px}
    50%{left:310px}
    100%{left:10px}
  }
  .roundLeft{
    margin-top: 10px;
    margin-left: 10px;
  }
  .roundRight{
    margin-left: 310px;
    margin-top: 10px;
  }

</style>