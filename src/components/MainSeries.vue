<script>
import axios from 'axios';
export default {
data() {
return {
    stars: [],
    emptyStars: [],
    tvCastNames: [],
}
},
props: {
    tvInfo: {
        type: Object,
        required: true,
    }
},
methods: {
    getStars(){
        const starNumber = parseInt(Math.ceil(this.tvInfo.vote_average) / 2, 10);
        for (let index = 0; index < starNumber; index++) {
            this.stars.push(index)
        };
        for (let index = starNumber; index < 5; index++) {
            this.emptyStars.push(index)
        };
    },
    getCast(){
        axios.get(`https://api.themoviedb.org/3/tv/${this.tvInfo.id}/credits`,{
            params: {
                api_key: '83724394da4505a6dc047ce5485571d4',
            }
        })
        .then( (response) => {
            let castList = response.data.cast;
            for (let index = 0; index < 5; index++) {
                this.tvCastNames.push(castList[index].name);
            };
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
    this.getCast();
},
}
</script>

<template>
    <li class="flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img :src="`https://image.tmdb.org/t/p/w342/${tvInfo.poster_path}`" alt="tv series poster">
            </div>
            <div class="flip-card-back">
                <div class="content">
                    <p>
                        Titiolo: {{ tvInfo.name }}
                    </p>
                    <p>
                        Titolo Originale: {{ tvInfo.original_name }}
                    </p>
                    <p>
                        Lingua: <span class="lang-icon" :class="`lang-icon-${tvInfo.original_language}`"></span>
                    </p>
                    <p>
                        overview: {{ tvInfo.overview }}
                    </p>
                    <div>
                        <ul class="stars">
                            <li v-for="(star, index) in stars" :key="index" class="star-color">
                                    <font-awesome-icon icon="fa-solid fa-star" />
                            </li>
                            <li v-for="(star, index) in emptyStars" :key="index">
                                    <font-awesome-icon icon="fa-solid fa-star" class="empty-star"/>
                            </li>
                        </ul>
                    </div>
                    <ul class="cast-list">
                            <li>
                                Cast:
                            </li>
                            <li v-for="(name,index) in tvCastNames" :key="index">
                                {{ name }}
                            </li>
                        </ul>
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