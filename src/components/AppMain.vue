<script>
import axios from 'axios';
import { store } from '../store.js';
import MainSearch from './MainSearch.vue';
import { info } from 'sass';

export default {
    components: {
        MainSearch,
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
            console.log(response.data.results);
            this.store.filmInfo = response.data.results;
        })
        .catch(function (error) {
        })
        .finally(function () {
            // always executed
        });  
    },
    info(film){
        console.log(film)
        this.getFilmInfo(this.apiFilmUrl, film)
    }
},
created() {
    this.getFilmInfo(this.apiFilmUrl)
}
}
</script>

<template>
    <MainSearch @searched="info"/>
</template>

<style scoped>

</style>