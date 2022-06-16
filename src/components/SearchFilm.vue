<template>
    <section class="d-flex flex-wrap gap-3">
        <FilmVue v-for="(film) in films" :key="film.id" :film="film" />
        <SerieVue v-for="(serie) in series" :key="serie.id" :serie="serie" />
    </section>
</template>

<script>
import FilmVue from './Film.vue';
import SerieVue from './Serie.vue';
export default {
    name: "SearchFilmVue",
    components: { FilmVue, SerieVue },
    props: {
        films: Array,
        series: Array
    }
}
</script>

<style scoped lang="scss">
section {
    width: 100%;
    padding: 0 10px;
    margin: 20px 0;
}
</style>