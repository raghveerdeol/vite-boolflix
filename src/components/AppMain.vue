<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
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
                query: 'ritorno al futuro',
            }
        })
        .then(function (response) {
            console.log(response.data.results);
            this.store.filmInfo = response.data.results;
        })
        .catch(function (error) {
            console.log(error);
        })
        .finally(function () {
            // always executed
        });  
            },
},
created() {
    this.getFilmInfo(this.apiFilmUrl)
}
}
</script>

<template>

</template>

<style scoped>

</style>