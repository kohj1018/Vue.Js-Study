<template>

<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>굿방</title>
</head>
<body>
  <div class="black-bg" v-if="isModalOpen == true">
    <div class="white-bg">
      <h2>{{ rooms[currentIdx].title }}</h2>
      <p>{{ rooms[currentIdx].content }}</p>
      <button @click="isModalOpen = false">닫기</button>
    </div>
  </div>

  <h1>굿방</h1>


  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  
  <div v-for="(room, i) in rooms" :key="i" class="product-bg">
    <div @click="loadModal(i)">
      <img :src="room.image" class="room-img">
      <h2>{{ room.title }}</h2>
      <p>{{ room.price }} 만원</p>
    </div>
    <button @click="room.reportCnt++">허위매물신고</button>
    <span style="margin-left: 20px">신고수 : {{ room.reportCnt }}</span>
  </div>
</body>
</html>  

</template>

<script>

import data from './assets/oneroom.js'

export default {
  name: 'App',
  data(){
    return {
      menus : ['Home', 'Shop', 'About'],
      rooms: data,
      isModalOpen: false,
      currentIdx: 0
    }
  },
  methods : {
    loadModal(i) {
      this.isModalOpen = true
      this.currentIdx = i
    },
  },
  components: {

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background: darkslateblue;
  margin-top: 50px;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 50px;
}
.product-bg {
  margin-top: 100px;
}
.room-img {
  width: 80%;
  margin-top: 40px;
}

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;  padding: 20px;
}
.white-bg {
  width: 100%;  background: white;
  border-radius: 8px;
  padding: 20px;
}

</style>
