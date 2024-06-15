<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
data() {
return {
        store,
}
},
props: {
    movieInfo: {
        type: Object,
        required: true,
    }
}
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
            </div>
        </li>
</template>

<style lang="scss" scoped>
@use '../styles/partials/flags' as *;
.lang-icon {
            background-image: url(../../node_modules/@textabledev/langs-flags-list/lang-flags.png);
}
</style>