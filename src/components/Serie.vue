<template>
    <div class="d-flex flex-column align-items-center col-2 text-center">
        <img :src="'https://image.tmdb.org/t/p/w92' + serie.poster_path" alt="">
        <h3>Nome: {{ serie.name }}</h3>
        <h4>Nome originale: {{ serie.original_name }}</h4>
        <span>Lingua originale: {{ serie.original_language }}
            <lang-flag :iso="serie.original_language" />
        </span>
        <span>Voto: {{ serie.vote_average }}</span>
        <span>serie</span>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'SerieVue',
    components: {
        LangFlag
    },
    props: {
        serie: Object
    }
}
</script>

<style scoped lang="scss">
div {
    background-color: aqua;
    border-radius: 20px;
}
</style>