<script>
import axios from 'axios';
import { store } from '../store.js';
import MainSearch from './MainSearch.vue';
import MainFilmInfo from './MainFilmInfo.vue'

export default {
    components: {
        MainSearch,
        MainFilmInfo,
    },
data() {
return {
    store,
    apiFilmUrl: 'https://api.themoviedb.org/3/search/movie'
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
    },
    movieName(film){
        console.log(film)
        this.getFilmInfo(this.apiFilmUrl, film)
    }
},
// created() {
//     this.getFilmInfo(this.apiFilmUrl)
// }
}
</script>

<template>
    <MainSearch @searched="movieName"/>
    <ul>
        <MainFilmInfo v-for="film in store.filmInfo" :movie-info="film"/>
    </ul>
</template>

<style lang="scss" scoped>
@use '../styles/generle.scss' as *;

</style>