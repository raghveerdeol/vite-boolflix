<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
data() {
return {
        store,
        stars: [],
}
},
props: {
    movieInfo: {
        type: Object,
        required: true,
    }
},
methods: {
    getStars(){
        const starNumber = (Math.round(parseInt(this.movieInfo.vote_average / 2, 10)));
        for (let index = 0; index < starNumber; index++) {
            this.stars.push(index)
        }
        console.log(this.stars)
    }
},
created(){
    this.getStars();
},
}
</script>

<template>
        <li>
            <img :src="`https://image.tmdb.org/t/p/w342/${movieInfo.poster_path}`" alt="movie poster">
            <div>
                Titiolo: {{ movieInfo.title }}
            </div>
            <div>
                Titolo Originale: {{ movieInfo.original_title }}
            </div>
            <div>
                Lingua: <span class="lang-icon" :class="`lang-icon-${movieInfo.original_language}`"></span>
            </div>
            <div>
                Voto: {{ movieInfo.vote_average }}
                <ul>
                    <li v-for="(star, index) in stars" :key="index">
                        star
                    </li>
                </ul>
            </div>
        </li>
</template>

<style lang="scss" scoped>
@use '../styles/partials/flags' as *;
.lang-icon {
            background-image: url(../../node_modules/@textabledev/langs-flags-list/lang-flags.png);
}
</style>