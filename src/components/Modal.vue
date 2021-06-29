<template>
    <div class="black-bg" v-if="modal_open == true">
        <div class="white-bg">
          <h4>{{room[itemNumber].title}}</h4>
          <img :src='room[itemNumber].image' class='thumbnail' alt='썸네일'>
          <p>{{room[itemNumber].price}}</p>
          <p>{{room[itemNumber].content}}</p>
          <Discount/>
          <!-- <button @click='modal_open =false'>닫기</button> -->
        </div>
      </div>
</template>

<script>
export default {
    name : 'Modal',
    props : {
        room : Array,
        itemNumber : Number,
        modal_open : Boolean,
    }
}
</script>

<style>
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
</style>