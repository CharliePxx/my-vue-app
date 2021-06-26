<template>
  <div class="box">
<!--    <ol>-->
<!--      <li v-for="item in list" :key="item">-->
<!--        {{item}}-->
<!--      </li>-->
<!--      <li v-for="(item, index) in list" :key="index">-->
<!--        {{item}}-->
<!--        {{index}}-->
<!--      </li>-->
<!--    </ol>-->
    <select>
      <option v-for="(item, index) in list" :key="index">
        {{item}}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "recircle",
  data(){
    return{
      list:[
        'a',
        'b',
        'c',
        'd'
      ]
    }
  }
}
</script>

<style scoped>


</style>