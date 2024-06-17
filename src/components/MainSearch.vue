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
    <div class="search">
        <input type="text" v-model="title" placeholder="search...">
        <button @click="$emit('searched', title)">search</button>
    </div>
</template>

<style lang="scss" scoped>
.search{
    display: flex;
    justify-content: flex-end;
    width: 80%;
    input{
        padding: .4rem 1.5rem;
        border: none;
        border-radius: 5px;
    }
    button{
        margin-left: 2rem;
        border: none;
        border-radius: 5px;
        padding: .4rem 1rem;
        text-transform: uppercase;
        font-weight: 700;
        background-color: whitesmoke;
    }
}
</style>