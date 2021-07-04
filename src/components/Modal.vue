<template>
    <div class="black-bg" v-if="modal_open == true">
        <div class="white-bg">
          <h4>{{room[itemNumber].title}}</h4>
          <img :src='room[itemNumber].image' class='thumbnail' alt='썸네일'>
          <p>{{room[itemNumber].content}}</p>
          <input type="text" onKeyup="this.value=this.value.replace(/[^0-9]/g,'');"  v-model.number="month">
          <p>{{ month }} 개월 선택함 : {{room[itemNumber].price * month}} 원</p>
          <button @click="$emit('closeModal')">닫기</button>
        </div>
      </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
      return {
        month : 1,
      }
    },
    watch : {
      month(a){
        if (a > 12){
          this.month = 1;
          alert('12달 까지만 입력이 가능합니다.');
        }
      }
    },
    props : {
        room : Array,
        itemNumber : Number,
        modal_open : Boolean,
    },
    methods : {
      close(){
        this.$emit('closeModal')
      }
    }
}
</script>

<style>

</style>