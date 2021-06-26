<template>
  <div class="body">
    <div class="banner">
      <div class="logo">
        <img src="../../public/static/huawei_logo.png" height="45" width="199.5"/>
      </div>
      <ul class="nav" v-for="(item,idx) in items" :key="idx">
        <li>{{item}}</li>
      </ul>
    </div>
    <div class="window" @mouseover="stop" @mouseleave="start">
      <div
          class="item"
          :key="idx"
          :style="`
        left: ${ (3380*(idx - count - 1) )% 600 + 200 }px;
        background: ${ item.color };
        z-index: ${ (3380*(idx - count - 1) )% 600 + 200 === 0 ? 999 : 0 };
      `"
      >

      </div>
      <div class="button">
        <div class="left" @click="left">&lt;</div>
        <div class="right" @click="right">&gt;</div>
      </div>
    </div>
    <div class="product"></div>
  </div>
</template>

<script>
export default {
  name: "huaweiWeb",
  components: {},
  data() {
    return {
      items:[
          '个人家庭及产品',
          '商用产品及方案',
          '服务支持',
          '合作伙伴与开发者',
          '关于华为',
      ],
      count:999,
    }
  },
  methods: {},
  mounted() {
  }
}
</script>

<style scoped>
  .banner{
    height: 58px;
    width: 100vw;
    background: white;
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
  }
  .logo{
    width: 133px;
    height: 66px;
    margin-left: 80px;
    margin-top: 30px;
  }
  .nav{
    display: flex;
    position: relative;
    left: 150px;
    top: 15px;
    height: 50px;
    width: 150px;

  }
  .nav li {
    flex: 1;
    vertical-align: middle;
    margin-top: 15px;
    list-style: none;
    font-size: 17px;
  }
  .window {
    margin: 0;
    height: 511px;
    width: 100vw;
    outline: 1px solid red;
    position: relative;
    /*left: 400px;*/
    top: 90px;
    overflow: hidden;
  }
  .window:hover .right{
    transition: 1s;
    display: block;
  }
  .window:hover .left{
    transition: 1s;
    display: block;
  }
  .window *{
    cursor: pointer;
  }
  .item {
    height: 120px;
    width: 200px;
    text-align: center;
    line-height: 120px;
    font-size: 100px;
    font-weight: bold;
    position: absolute;
    top: 0px;
    left: 0;
    transition: .5s linear;
    /*background-image:url("public/static/hwcloud-618-2.jpg");*/
  }
  .button{
    height: 50px;
    width: 200px;
    /*background: black;*/
    /*border: 2px solid black;*/
    z-index: 1500;
    position: absolute;
  }
  .left{
    width: 50px;
    height: 25px;
    /*float: left;*/
    /*border: 1px solid black;*/
    text-align: center;
    color: black;
    position: absolute;
    top: 30px;
    left:0;
    display: none;
  }
  .right{
    width: 50px;
    height: 25px;
    /*float: left;*/
    /*border: 1px solid black;*/
    text-align: center;
    color: black;
    position: absolute;
    top:30px;
    left:150px;
    display: none;
  }
  </style>