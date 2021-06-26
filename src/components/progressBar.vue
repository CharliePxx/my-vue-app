<template>
  <div class="window" @mouseover="stop" @mouseleave="start">

    <div
        class="item"
        v-for="(item, idx) in list"
        :key="idx"
        :style="`
        left: ${ (200 * idx - 200 * count - 200) % 600 + 200 }px;
        background: ${ item.src };
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
  <div class="progresses">
    <div class="container" v-for="(item,idx) in widthList" :key="idx">
      <div class="inner" :style="`width:${item}px;opacity:${item===0?0:1}`"> </div>
    </div>
  </div>
</template>

<script>
let clickable = true;
export default {
  name: "progress bar",
  components: {},
  data() {
    return {
      widthList:[0,0,0],//[width,width,width]
      currentIndex:0,
      list:[
        {
          content: '1',
          src:'/static/vmall-618.jpg',
          color: 'red',
        },
        {
          content: '2',
          src:'https://cn.bing.com/images/search?view=detailV2&ccid=M2dHJdmu&id=70CE23C59FEE69C879EE57BD76FB7EEEF5C2BD3D&thid=OIP.M2dHJdmuNPhuODWuMLIK_gHaEo&mediaurl=https%3a%2f%2fth.bing.com%2fth%2fid%2fR33674725d9ae34f86e3835ae30b20afe%3frik%3dPb3C9e5%252b%252b3a9Vw%26riu%3dhttp%253a%252f%252fwww.desktx.com%252fd%252ffile%252fwallpaper%252fscenery%252f20180626%252f4c8157d07c14a30fd76f9bc110b1314e.jpg%26ehk%3d9tpmnrrRNi0eBGq3CnhwvuU8PPmKuy1Yma0zL%252ba14T0%253d%26risl%3d%26pid%3dImgRaw&exph=1200&expw=1920&q=%e5%9b%be%e7%89%87&simid=607989652082148254&ck=E5351C90A23376085FC39502FAB5EFCC&selectedIndex=0&FORM=IRPRST',
          color: 'green',
        },
        {
          content: '3',
          src:'https://cn.bing.com/images/search?view=detailV2&ccid=UKwOpMvA&id=B66D04874178CFA5820B2DA6996C2BFEC81E5004&thid=OIP.UKwOpMvAgVz63mAzQEVjYwHaE8&mediaurl=https%3a%2f%2fth.bing.com%2fth%2fid%2fR50ac0ea4cbc0815cfade603340456363%3frik%3dBFAeyP4rbJmmLQ%26riu%3dhttp%253a%252f%252fimg10.3lian.com%252fsc6%252fshow02%252f38%252f65%252f386503.jpg%26ehk%3dEMia04qW2ddUCswLrH8oE1JLdQBeMBtpVrWMBvMMOW4%253d%26risl%3d%26pid%3dImgRaw&exph=427&expw=640&q=%e5%9b%be%e7%89%87&simid=608028521520632449&ck=856BDA64513840FBBDFFD17527E7E4EC&selectedIndex=5&FORM=IRPRST',
          color: 'blue',
        },
      ],
      count: 999,
      counter:"",
      // clickable: true,
    }
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
  mounted() {
    setInterval(()=>{
      this.widthList[this.currentIndex]=100;
      this.widthList[this.currentIndex-1<0?this.widthList.length-1:this.currentIndex-1]=0;
      if (this.currentIndex === this.widthList.length-1){
        this.currentIndex=0;
      }else{
        this.currentIndex++;
      }
      //使用数组代替原有数组触发更新
      this.widthList= this.widthList.concat();
    },1000)
    this.start()
    }
}
<img src="../../public/static/FreeBuds_4_cn.jpg" height="550" width="550"/></script>

<style scoped>
.window {
  height: 120px;
  width: 200px;
  outline: 1px solid red;
  position: absolute;
  left: 50%;
  top:300px;
  transform: translate(-50%,-50%);
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
.progresses{
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
}
.container{
  height: 3px;
  width: 100px;
  background: #aaa;
  float: left;
  margin-left: 16px;
}
.inner{
  height: 3px;
  width: 0px;
  background: white;
  transition: width 1s linear;
}
</style>