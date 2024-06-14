<script>
import axios from 'axios';
import { store } from '../store.js';
import MainSearch from './MainSearch.vue';
import MainFilmInfo from './MainFilmInfo.vue'
import MainSeries from './MainSeries.vue'

export default {
    components: {
        MainSearch,
        MainFilmInfo,
        MainSeries,
    },
data() {
return {
    store,
    apiFilmUrl: 'https://api.themoviedb.org/3/search/movie',
    apitvUrl: 'https://api.themoviedb.org/3/search/tv',
}
},
methods: {
    getFilmInfo(url, filmName){
        axios.get(url, {
            params: {
                api_key: '83724394da4505a6dc047ce5485571d4',
                query: filmName,
            }
        })
        .then(function (response) {
            store.filmInfo = response.data.results;
            console.log(response.data.results);
        })
        .catch(function (error) {
        })
        .finally(function () {
            // always executed
        });  
    },getTvsSeries(url, seriesName){
        axios.get(url,{
            params: {
                api_key: '83724394da4505a6dc047ce5485571d4',
                query: seriesName,
            }
        })
        .then(function(response){
            store.seriesInfo = response.data.results;
            console.log(response.data.results);
        })
        .catch(function (error) {
        })
        .finally(function () {
            // always executed
        });  
    },
    movieName(title){
        console.log(title)
        this.getFilmInfo(this.apiFilmUrl, title)
        this.getTvsSeries(this.apitvUrl, title)
    }
},
}
</script>

<template>
    <MainSearch @searched="movieName"/>
    <ul>
        <MainFilmInfo v-for="film in store.filmInfo" :movie-info="film"/>
    </ul>
    <ul>
        <MainSeries v-for="series in store.seriesInfo" :tv-info="series" />
    </ul>
</template>

<style lang="scss" scoped>
@use '../styles/generle.scss' as *;

</style>