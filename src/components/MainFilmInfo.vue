<script>
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
            <div>
                Titiolo: {{ movieInfo.title }}
            </div>
            <div>
                Titolo Originale: {{ movieInfo.original_title }}
            </div>
            <div>
                Lingua: {{ movieInfo.original_language }}
            </div>
            <div>
                Voto: {{ movieInfo.vote_average }}
            </div>
        </li>
</template>

<style scoped>

</style>