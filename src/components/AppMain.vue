<script>
import axios from 'axios';
import { store } from '../store.js';
import MainFilmInfo from './MainFilmInfo.vue'
import MainSeries from './MainSeries.vue'

export default {
    components: {
        MainFilmInfo,
        MainSeries,
    },
data() {
return {
    store,
}
}
}
</script>

<template>
    <div class="main-container">
        <h2>Films</h2>
        <ul>
            <MainFilmInfo v-for="film in store.filmInfo" :movie-info="film"/>
        </ul>
        <h2>Tv Series</h2>
        <ul>
            <MainSeries v-for="series in store.seriesInfo" :tv-info="series" />
        </ul>
    </div>
</template>

<style lang="scss" scoped>
@use '../styles/partials/mixins' as *;
@use '../styles/partials/variables' as *;
.main-container{
    max-width: 80%;
    margin: 0 auto;
}
ul{
    @include flex-between;
    flex-wrap: wrap;
}
h2{
    color: red;
    padding: 1rem 0;
    font-weight: 900;
    text-align: center;
    font-size: 2rem;
}
</style>