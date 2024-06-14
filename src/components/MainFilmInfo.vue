<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
data() {
return {
        store,
}
},
methods: {
    urlFlag(language){
        // if (language.value === en) {
        //     return 'https://flagsapi.com/GB/flat/64.png'
        // } else {
            return 'https://flagsapi.com/' + language.toUpperCase() + '/flat/24.png'
        // }
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
            <div>
                Titiolo: {{ movieInfo.title }}
            </div>
            <div>
                Titolo Originale: {{ movieInfo.original_title }}
            </div>
            <div>
                Lingua: {{ movieInfo.original_language }}
                <span class="lang-icon lang-icon-en"></span>
            </div>
            <div>
                Voto: {{ movieInfo.vote_average }}
            </div>
        </li>
</template>

<style scoped>

</style>