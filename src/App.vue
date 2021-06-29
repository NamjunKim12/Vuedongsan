<template>

<Modal :room='room' :itemNumber = 'itemNumber' modal_open = 'modal_open'/>

<div class="menu">
  <a v-for="category in menu" :key="category">{{category}}</a>
</div>

<Discount/>

  <div class='item_container' v-for='(a, i) in room' :key="i" >
    <div class='item' >
      <img @click = "modal_open = true; itemNumber = i" :src='a.image' class='thumbnail' alt='썸네일'>
      <h4 @click = "modal_open = true; itemNumber = i">{{a.title}}</h4>
      <p>{{a.price}}</p>
    </div>
  </div>

</template>

<script>

import roomData from './assets/oneroom.js';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';


export default {
  name: 'App',
  data(){
    return{
      room : roomData,
      itemNumber : 0,
      menu : ['Home','Shop', 'About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸'],
      price : [50, 60, 70],
      modal_open : false,
      

    }
  },
  methods:{

},
  components: {
    Discount : Discount,
    Modal : Modal,
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

img{
  width: 450px;
  height: 250px;
}



</style>
