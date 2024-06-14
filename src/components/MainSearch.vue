<script>
export default {
data() {
return {
    film: '',
}
}
}
</script>

<template>
    <input type="text" v-model="film">
    <button @click="$emit('searched', film)">search</button>
</template>

<style scoped>

</style>