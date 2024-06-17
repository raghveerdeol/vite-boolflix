<script>
export default {
data() {
return {
    stars: [],
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
        const starNumber = Math.round(parseInt(this.tvInfo.vote_average / 2, 10));
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
        <img :src="`https://image.tmdb.org/t/p/w342/${tvInfo.poster_path}`" alt="tv series poster">
            <div>
                Titiolo: {{ tvInfo.name }}
            </div>
            <div>
                Titolo Originale: {{ tvInfo.original_name }}
            </div>
            <div>
                Lingua: <span class="lang-icon" :class="`lang-icon-${tvInfo.original_language}`"></span>
            </div>
            <div>
                Voto: {{ tvInfo.vote_average }}
                <ul>
                    <li v-for="(star, index) in stars" :key="index">
                        <div id="app">
                            <!-- Add the style and icon you want using the String format -->
                            <font-awesome-icon icon="fa-solid fa-star" />
                        </div>
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