<template>

  <div class="black-bg" v-if="isOpenModal" @click="closeModal">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="작명 in 3" :key="작명">Home</a>
    <a v-for="(menu, index) in menus" :key="index">{{ menu }}</a>
  </div>
  <div v-for="(product, i) in products" :key="i">
    <img src="./assets/room0.jpg" alt="img" class="roomImg">
    <h4 @click="openModal">{{product}}</h4>
    <p>{{price1}} 만원</p>
    <button @click="increase(i)">허위매물신고</button> <span>신고수: {{ counts[i] }}</span>
  </div>
  <div v-for="room in rooms" :key="room">
    <img :src=room.image :alt=room.id class="roomImg">
    <h4>{{ room.title }}</h4>
    <p>{{ room.content }}</p>
    <p>{{ room.price.toLocaleString() }} 원</p>
  </div>
</template>

<script>

import post from './data/post'

export default {
  name: 'App',
  data(){
    return{
      price1 : 60,
      price2 : 70,
      스타일 : 'color : blue',
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      counts : [0, 0, 0],
      isOpenModal : false,
      rooms : post,
    }
  },
  methods : {
    increase(i){
      this.counts[i]++
    },
    openModal(){
      this.isOpenModal = true
    },
    closeModal(){
      this.isOpenModal = false
    }
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
}

body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, .5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
.roomImg{
  width: 100%;
  margin-top: 40px;
}
</style>
