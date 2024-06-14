<script>
export default {
data() {
return {

}
},
props: {
    tvInfo: {
        type: Object,
        required: true,
    }
}
}
</script>

<template>
    <li>
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
            </div>
        </li>
</template>

<style lang="scss" scoped>
@use '../styles/partials/flags' as *;
.lang-icon {
            background-image: url(../../node_modules/@textabledev/langs-flags-list/lang-flags.png);
}
</style>