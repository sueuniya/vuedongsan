<template>

<!-- :작명가능한것 = "밑에있는데이터랑 똑같이 설정 가능 " -->
<Transition name="fade">
  <Modal :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" @close = "모달창열렸니 = false;"/>
</Transition>>

<div class="menu">
  <a href="#">Home</a>
  <a href="#">FAQ</a>
  <a href="#">List</a>
</div>


<Discount/>

<button @click="priceSort">가격순정렬</button>

<!-- <Card v-for="(item, i) in 원룸들" :key="i" :item="item" /> -->
  <!-- <div v-for="(item , i ) in product∫" :key="item">
    <img :src="require(`./assets/${picture[i]}`)" :alt="picture[i]" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ products[i] }}</h4>
    <p>{{ price[i] }} 만원</p>
    <button @click="increase(i) ">허위매물신고</button>
    <span>신고수: {{ 신고수[i] }}</span>
  </div>  -->

  
  <!-- <div> -->
    <!-- <img :src="원름들[0].image" alt=""> -->`
    <!-- <h4>{{ 원룸들[0].title }}</h4> -->
    <!-- <p>{{ 원름들[0].price }}원</p> -->
    
    <Card2 v-for = "naming in 원룸들" key = "naming" :taking="naming" @openModal="모달창열렸니 = true; 누른거=$event"/>

    <!-- @작명 (자식 $emit 작명 이름 가져옴) = "스크립트 식 등등 모두 넣을수있음" -->
    <!-- <Card2 :taking="원룸들[0]" /> -->
  
</template>

<script>
import data from './assets/oneroom.js';
import Discount from './components/Discount';
import Modal from './components/Modal';
import Card from './components/Card';
import Card2 from './components/Card2';


export default {
  name : 'App',
  data(){
    return {
      원룸들오지지널: '', 
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0 ,0,0],
      메뉴들 : ['home','shop','About'],
      products : [ '역삼동원룸' , '천호동원룸' ,'마포구원룸'],
      price : [ '10' , '20' ,'10'],
      picture: ['room0.jpg','room1.jpg','room2.jpg']
    }
  },
  methods : {
    increase(i){
     this.신고수[i] ++ 
     // this 여기안에서 데이터를 쓰고싶을 때 추가해야함
    },
    sortBack(){
      this.원룸들 = this.원룸들오리지널;
    },
    priceSort() {
      this.원룸들.sort(function(a,b){
        return a.price - b.price 
      })
      // sort 는 원형이 변경되지만 map이나 filter를 사용하면 원본데이터 보존
    },
  },
  components: {
    Discount : Discount,
    Modal,
    Card ,
    Card2
  }
}

</script>

<style>
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 

.menu {
  background-color: lightpink;
  padding: 10px 20px;
  border-radius: 10px;
}

.menu a {
  color: #fff;
  font-size: 20px;
  padding: 20px;
  
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
.discount {
  background: #eee;
  padding: 20px;
  margin: 10px;
  border-radius: 20px;
}

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all .3s;
}
.fade-enter-to {
  opacity: 1;
  transform: translateY(0px);
}
</style>