<template>
    <div class='item' >
        <img @click="$emit('openModal', room.id)" :src='room.image' class='thumbnail' alt='썸네일'>
        <h4 @click="$emit('openModal', room.id)">{{room.title}}</h4>
        <p>{{room.price}} 원</p>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props : {
        room : Object,
        modal_open : Boolean,

    },
    methods : {
        open(){
            this.$emit('openModal', this.room.id)
        }
    }
}
</script>

<style>

</style>