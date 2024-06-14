<script>
export default {
data() {
return {
    title: '',
}
}
}
</script>

<template>
    <input type="text" v-model="title">
    <button @click="$emit('searched', title)">search</button>
</template>

<style scoped>

</style>