<template>
    <div class="d-flex flex-column align-items-center col-2 text-center">
        <img v-if="film.poster_path !== null" :src="'https://image.tmdb.org/t/p/w92' + film.poster_path" alt="">
        <h3>Titolo: {{ film.title }}</h3>
        <h4>Titolo originale: {{ film.original_title }}</h4>
        <span>Lingua originale: {{ film.original_language }}
            <lang-flag :iso="film.original_language" />
        </span>
        <span>
            <font-awesome-icon icon="fa-solid fa-star" v-for="(star, index) in ratingStar" :key="index" />
            <font-awesome-icon icon="fa-regular fa-star" v-for="(star, index) in (5 - ratingStar)" :key="index" />
        </span>
        <span>film</span>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'FilmVue',
    components: {
        LangFlag
    },
    props: {
        film: Object
    },
    computed: {
        ratingStar() {
            return Math.ceil(this.film.vote_average / 2);
        }
    }
}
</script>

<style scoped lang="scss">
div {
    background-color: aqua;
    border-radius: 20px;
}
</style>