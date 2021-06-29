<template>
    <div class='item' >
        <img :src='room.image' class='thumbnail' alt='썸네일'>
        <h4 >{{room.title}}</h4>
        <p>{{room.price}}</p>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props : {
        room : Object,
    }
}
</script>

<style>

</style>