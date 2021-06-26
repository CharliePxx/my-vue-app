<template>
<!--  <div v-if="visible" class="box"></div>-->
  <box v-if="visible"></box>
  <button @click="toggle">点击隐藏</button>
</template>

<script>
import box from "@/components/box";
export default {
  name: "buttonVisible",
  components:{
    box
  },
  data(){
    return{
      visible:false
    }
  },
  methods:{
    toggle(){
      this.visible = !this.visible
    }

  }

}
</script>

<style scoped>
  /*.box{*/
  /*  width: 100px;*/
  /*  height: 100px;*/
  /*  background: black;*/
  /*}*/
  /*button{*/
  /*  position: fixed;*/
  /*  top: 110px;*/
  /*}*/

</style>