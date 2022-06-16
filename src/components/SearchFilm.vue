<template>
    <section>
        <h2>Risultati della ricerca:</h2>
        <div class="d-flex flex-wrap">
            <FilmVue v-for="(film) in films" :key="film.id" :film="film" />
            <SerieVue v-for="(serie) in series" :key="serie.id" :serie="serie" />
        </div>
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
    margin: 90px 0;

    h2 {
        color: white;
    }
}
</style>