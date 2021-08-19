<template>
    <div>
        <h4>{{제품데이터.title}}</h4>
        <p>{{제품데이터.caption}}</p>
        <img :src="제품데이터.img" :alt="제품데이터.title">
        <p>{{제품데이터.price}}</p>
        <span>{{제품데이터}}</span>
    </div>
</template>

<script>
export default {
    props:{
        제품데이터:Array
    },
}
</script>

<style>

</style>