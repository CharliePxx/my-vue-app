<template>
  <div class="light">
    <div :class="'redLight '+ color1">

    </div>
    <div :class="'greenLight '+ color2">

    </div>
   <button @click="onClick">click</button>
  </div>
</template>

<script>
export default {
  name: "changeLight",
  data(){
    return{
      color1:'red',
      color2: 'beige'
    }
  },
  methods:{
    onClick(){
      if (this.color1 === 'red'){
        this.color1 = 'beige'
        this.color2 = 'green'
      }else{
        this.color1 = 'red'
        this.color2 = 'beige'
      }
    },
  },
  mounted(){

  }
}
</script>

<style scoped>
  .light{
    display: flex;
    height: 200px;
    width: 600px;
    border: 2px solid black;
  }
  .redLight{
    height: 150px;
    width: 150px;
    border: 2px solid black;
    border-radius: 50%;
  }
  .greenLight{
    /*margin-left: 200px;*/
    height: 150px;
    width: 150px;
    border: 2px solid black;
    border-radius: 50%;
  }
  button{
    height: 50px;
  }
  .red{
    background: red;
  }
  .green{
    background: green;
  }
  .beige{
    background: beige;
  }


</style>