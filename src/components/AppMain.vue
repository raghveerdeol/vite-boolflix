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
    <h2>Films</h2>
    <ul>
        <MainFilmInfo v-for="film in store.filmInfo" :movie-info="film"/>
    </ul>
    <h2>Tv Series</h2>
    <ul>
        <MainSeries v-for="series in store.seriesInfo" :tv-info="series" />
    </ul>
</template>

<style lang="scss" scoped>


</style>