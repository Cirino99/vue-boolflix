<template>
    <section>
        <h2>Film popolari</h2>
        <div class="d-flex flex-wrap justify-content-between">
            <FilmVue v-for="(film) in popularFilms" :key="film.id" :film="film" />
        </div>
        <h2>Top film</h2>
        <div class="d-flex flex-wrap justify-content-between">
            <FilmVue v-for="(film) in topFilms" :key="film.id" :film="film" />
        </div>
        <h2>Serie popolari</h2>
        <div class="d-flex flex-wrap justify-content-between">
            <SerieVue v-for="(serie) in popularSeries" :key="serie.id" :serie="serie" />
        </div>
        <h2>Top serie</h2>
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

    h2 {
        color: white;
        margin-top: 30px;
        margin-bottom: 10px;
    }

    div {
        gap: 20px 0;
    }
}
</style> 