<template>

    <Modal @closeModal="modal_open = false;" :room="room" :itemNumber="itemNumber" :modal_open="modal_open"/>

    <div class="menu">
      <a v-for="category in menu" :key="category">{{category}}</a>
    </div>

    <Discount/>

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
      room : roomData,
      itemNumber : 0,
      menu : ['Home','Shop', 'About'],
      modal_open : false,
    }
  },
  methods:{

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
