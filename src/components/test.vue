<template>
  <div>

    <div class="window">

      <div
          class="item"
          v-for="(item, idx) in list"
          :key="idx"
          :style="`
          left: ${ (100 * idx - 100 * count - 100) % (100 * list.length) + 100 }vw;
          background: ${ item.src };
          z-index: ${ (100 * idx - 100 * count - 100) % (100 * list.length) + 100 === 0 ? 999 : 0 };
        `"
      >

        <img :src="item.src" alt="">
      </div>

      <div class="sliders">
        <div
            class="container"
            v-for="(item, idx) in widthList"
            :key="idx"
        >
          <div class="inner" :style="`width:${item}px; opacity: ${item === 0 ? 0 : 1};`"></div>
        </div>
      </div>


    </div>


  </div>
</template>

<script>
export default {
  data () {
    return {
      widthList: [0, 0, 0], // [width, width, width]
      currentIndex: 0,
      count: 0,
      list:[
        {
          src: 'https://img2.baidu.com/it/u=3206689113,2237998950&fm=26&fmt=auto&gp=0.jpg',
          color: 'red',
        },
        {
          src: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.pconline.com.cn%2Fimages%2Fupload%2Fupc%2Ftx%2Fphotoblog%2F1402%2F07%2Fc7%2F31066355_31066355_1391779709500_mthumb.jpg&refer=http%3A%2F%2Fimg.pconline.com.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1626681764&t=a6e0341b1d8a07f249924f2bde905acd',
          color: 'green',
        },
        {
          src: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.pconline.com.cn%2Fimages%2Fupload%2Fupc%2Ftx%2Fphotoblog%2F1309%2F25%2Fc49%2F26316176_26316176_1380092693834_mthumb.jpg&refer=http%3A%2F%2Fimg.pconline.com.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1626681764&t=39337f6ba2138835e45eb7d9110f6403',
          color: 'blue',
        },
      ],
    };
  },
  methods: {
    update () {
      this.widthList[this.currentIndex] = 100;
      this.widthList[this.currentIndex - 1 < 0 ? this.widthList.length - 1 : this.currentIndex - 1] = 0;
      if (this.currentIndex === this.widthList.length - 1) {
        this.currentIndex = 0;
      } else {
        this.currentIndex++;
      }

      this.count++;

      // 使用新数组替换原有数组触发更新
      this.widthList = this.widthList.concat();
    },
  },
  mounted(){
    setTimeout(this.update, 1);
    setInterval(this.update, 3000);
  }
}
</script>

<style>
body {
  margin: 0;
}
.sliders {
  position: absolute;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 999999;
}
.container {
  height: 3px;
  width: 100px;
  /* #000 #111 >>> #eee #fff */
  background: #aaa;
  margin-left: 16px;
  float: left;

}
.inner {
  height: 3px;
  width: 0px;
  background: white;
  transition: width 3s linear;
}

.window {
  height: 600px;
  width: 100vw;
  position: relative;
  left: 0;
  overflow: hidden;
}
.window .item {
  height: 600px;
  width: 100vw;
  position: absolute;
  top: 0px;
  left: 0;
  transition: .5s linear;
  background: white;
}
.window img {
  width: 100%;
  height: 100%;
}
</style>