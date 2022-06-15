<template>
    <section class="d-flex flex-wrap gap-3">
        <FilmVue v-for="(film) in listFilms" :key="film.id" :film="film" />
    </section>
</template>

<script>
import FilmVue from './Film.vue';
export default {
    name: "SearchFilmVue",
    components: { FilmVue },
    props: {
        listFilms: Array
    }
}
</script>

<style scoped lang="scss">
</style>