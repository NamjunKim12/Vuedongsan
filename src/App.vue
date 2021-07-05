<template>
  <transition name="fade">
      <Modal @closeModal="modal_open = false;" 
      :room="room" 
      :itemNumber="itemNumber" 
      :modal_open="modal_open"/>
  </transition>

    <div class="menu">
      <a v-for="category in menu" :key="category">{{category}}</a>
    </div>

    <Discount :amount="amount" v-if="showDiscount == true"/>

    <button @click="priceSort()"> 가격오름차순정렬 </button>
    <button @click="priceSortReverse()"> 가격내림차순정렬 </button>
    <button @click="nameSort()"> 이름오름차순정렬 </button>
    <button @click="nameSortReverse()"> 이름내림차순정렬 </button>
    <button @click="sortBack()"> 되돌리기 </button>

    <Card @openModal="modal_open = true; itemNumber=$event"  :room="room[i]" v-for="(item, i) in room" :key="item"/>

</template>

<script>

import roomData from './assets/oneroom.js';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';




export default {
  name: 'App',
  data(){
    return{
      showDiscount : true, 
      roomOrigin : [...roomData],
      room : roomData,
      itemNumber : 0,
      menu : ['Home','Shop', 'About'],
      modal_open : false,
      amount: 30,

    }
  },
  methods:{
    priceSort(){
      this.room.sort(
        function(a,b){
          return a.price - b.price
        })
    },
    priceSortReverse(){
      this.room.sort(
        function(a,b){
          return b.price - a.price
        })
    },
    
    sortBack(){
      this.room = [...this.roomOrigin];
    },

    nameSort(){
      this.room.sort(
        function(a, b){
          if (a.title < b.title){
            return -1 
          } else {
            return 1
          }
        }
      )
    },
    nameSortReverse(){
      this.room.sort(
        function(a,b){
          if( a.title < b.title ){
            return 1
          } else {
            return -1
          }
        }
      )
    },

},

  mounted(){
    var timer = setInterval(()=>{
      this.amount--;
          if (this.amount === 0){
      clearInterval(timer)
      this.showDiscount = false;
    }
    },1000);
  },

  beforeUpdate(){
    if (this.month == 2){
      alert('2개월은 너무 적음.. 안팝니다')
    }
 },

  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
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

body {
  margin : 0;
}
div {
  box-sizing: border-box;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}


.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  transform: translate(50%, 20%);
  width: 50%; 
  background: white;
  border-radius: 8px;
  padding: 20px;
} 

.white-bg img{
  width: 80%;
  height:80%;
}

.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
  }

.item{
  margin-bottom: 20px;
  margin-top: 20px;
}

.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;

}

img{
  width: 450px;
  height: 250px;
}



</style>
