<template>
    <section>
        <h1>Film popolari</h1>
        <div class="d-flex flex-wrap justify-content-between">
            <FilmVue v-for="(film) in popularFilms" :key="film.id" :film="film" />
        </div>
        <h1>Top film</h1>
        <div class="d-flex flex-wrap justify-content-between">
            <FilmVue v-for="(film) in topFilms" :key="film.id" :film="film" />
        </div>
        <h1>Serie popolari</h1>
        <div class="d-flex flex-wrap justify-content-between">
            <SerieVue v-for="(serie) in popularSeries" :key="serie.id" :serie="serie" />
        </div>
        <h1>Top serie</h1>
        <div class="d-flex flex-wrap justify-content-between">
            <SerieVue v-for="(serie) in topSeries" :key="serie.id" :serie="serie" />
        </div>
    </section>
</template>

<script>
import FilmVue from './Film.vue';
import SerieVue from './Serie.vue';
export default {
    name: "HomeVue",
    components: { FilmVue, SerieVue },
    props: {
        popularFilms: Array,
        topFilms: Array,
        popularSeries: Array,
        topSeries: Array
    }
}
</script>

<style scoped lang="scss">
section {
    width: 100%;
    padding: 0 10px;
    margin: 90px 0;

    div {}
}
</style> 