<script>
import axios from 'axios';
import { store } from '../store.js';
import MainSearch from './MainSearch.vue';
import HeaderLogo from './HeaderLogo.vue';

export default {
    components: {
        HeaderLogo,
        MainSearch,
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
    },
    getTvsSeries(url, seriesName){
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
    <header>
        <div class="container">
            <HeaderLogo/>
            <MainSearch @searched="movieName"/>
        </div>
    </header>
</template>

<style lang="scss" scoped>
@use '../styles/partials/mixins' as*;
header{
    background-color: black;
}
.container{
    @include flex-between;
    max-width: 80%;
    margin: 0 auto;
    padding: 1.5rem 0;
}
</style>