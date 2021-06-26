<template>
  <div class="box">
    <input type="text" name="name" v-model="addContent">
    <button @click="addItem">add</button>
    <div class="table" v-for="(item, idx) in items" :key="idx">
      <div class="item">{{item}}</div>
      <button class="delButton" @click="deleteItem(idx)">delete</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "deleteTable",
  components: {},
  data() {
    return {
      items:['ice-cream','hotpot','shit','burger','chips'],
      addContent:''
    }
  },
  methods: {
    deleteItem(index){
      this.items.splice(index, 1)
    },
    addItem(){
      // eslint-disable-next-line no-unused-vars
      // var name = document.getElementById("name").value
      this.items.push(this.addContent)
      this.addContent=''

    }
  },
  mounted() {
  }
}
</script>

<style scoped>
.box{
  width: 200px;
  height: 500px;
  margin-bottom: 20px;
}
.table{
  width: 190px;
  height: 50px;
  /*border: 2px solid black;*/
  display: flex;
  align-items: center;
}
/*.delButton{*/
/*  width: 20px;*/
/*  height: 10px;*/
/*  border: 1px solid black;*/
/*}*/
button{
  margin-left: 10px;
}
</style>