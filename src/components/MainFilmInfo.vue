<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
data() {
return {
        store,
        stars: [],
        emptyStars: [],
        cast: [],
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
        const starNumber = parseInt(Math.ceil(this.movieInfo.vote_average) / 2, 10);
        for (let index = 0; index < starNumber; index++) {
            this.stars.push(index)
        };
        for (let index = starNumber; index < 5; index++) {
            this.emptyStars.push(index)
        }
    },
    getCast(){
        axios.get(`https://api.themoviedb.org/3/movie/${this.movieInfo.id}/credits`,{
            params: {
                api_key: '83724394da4505a6dc047ce5485571d4',
            }
        })
        .then(function (response) {
            let castList = response.data.cast;
            let list = [];
            for (let index = 0; index < 5; index++) {
                list.push(castList[index].name);
            };
            console.log(list);
            this.cast = list;
        })
        .catch(function (error) {
        })
        .finally(function () {
            // always executed
        });  
    },
},
created(){
    this.getStars();
    this.getCast()
},
}
</script>

<template>
    <p>{{ cast }}</p>
        <li class="flip-card">
            <div class="flip-card-inner">
                <div class="flip-card-front">
                    <img :src="`https://image.tmdb.org/t/p/w342/${movieInfo.poster_path}`" alt="movie poster">
                </div>
                <div class="flip-card-back">
                    <div class="content">
                        <p>
                            Titiolo: {{ movieInfo.title }}
                        </p>
                        <p>
                            Titolo Originale: {{ movieInfo.original_title }}
                        </p>
                        <p>
                            Lingua: <span class="lang-icon" :class="`lang-icon-${movieInfo.original_language}`"></span>
                        </p>
                        <p>
                            overview: {{ movieInfo.overview }}
                        </p>
                        <div>
                            <ul class="stars">
                                <li v-for="(star, index) in stars" :key="index" class="star-color">
                                        <font-awesome-icon icon="fa-solid fa-star" />
                                </li>
                                <li v-for="(star, index) in emptyStars" :key="index" >
                                        <font-awesome-icon icon="fa-solid fa-star" class="empty-star"/>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </li>
</template>

<style lang="scss" scoped>
@use '../styles/partials/flags' as *;
@use '../styles/partials/mixins' as *;
@use '../styles/partials/variables' as *;
@use '../styles/partials/cardsStyle' as *;
</style>