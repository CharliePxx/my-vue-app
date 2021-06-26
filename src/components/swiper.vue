<template>
  <div class="window" @mouseover="stop" @mouseleave="start">
    <div
        class="item"
        v-for="(item, idx) in list"
        :key="idx"
        :style="`
        left: ${ (200 * idx - 200 * count - 200) % 600 + 200 }px;
        background: ${ item.color };
        z-index: ${ (200 * idx - 200 * count - 200) % 600 + 200 === 0 ? 999 : 0 };
      `"
    >
      {{ item.content }}
    </div>
    <div class="button">
      <div class="left" @click="left">&lt;</div>
      <div class="right" @click="right">&gt;</div>
    </div>
  </div>
<!--  <div class="button">-->
<!--    <div class="left" @click="left">往左</div>-->
<!--    <div class="right" @click="right">往右</div>-->
<!--  </div>-->
</template>

<script>
//clickable这个变量没有用于网页渲染，所以没有必要写在data里
//直接声明
let clickable = true;
export default {
  name: "App",
  data() {
    return {
      list:[
        {
          content: '1',
          color: 'red',
        },
        {
          content: '2',
          color: 'green',
        },
        {
          content: '3',
          color: 'blue',
        },
      ],
      count: 999,
      counter:"",
      // clickable: true,
    };
  },
  methods: {
    abs (num) {
      return Math.abs(num);
    },
    stop(){
      clearInterval(this.counter);
    },
    start(){
      // this.count++;
      this.counter=setInterval(() => {
        this.count++;
      }, 1000);
    },
    left(){
      // this.stop()
      if(clickable){
        this.count --;
        this.setClickable()
      }
      // this.start();
    },
    right(){
      // this.stop();
      if(clickable){
        this.count ++;
        this.setClickable();
      }
      // this.start();
    },
    setClickable(){
      clickable = false;
      setInterval(() => {
        clickable=true;
      }, 1000);
    }
  },
  mounted () {
    this.start()
  },
};
</script>

<style>
.window {
  height: 120px;
  width: 200px;
  outline: 1px solid red;
  position: relative;
  left: 400px;
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
  background: white;
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