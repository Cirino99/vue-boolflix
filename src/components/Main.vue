<template>
    <main>
        <ul>
            <li v-for="(film) in listFilms" :key="film.id">
                <FilmVue :film="film" />
            </li>
        </ul>

    </main>
</template>

<script>
import FilmVue from './Film.vue';
export default {
    name: "MainVue",
    components: { FilmVue },
    props: {
        listFilms: Array
    }
}
</script>

<style scoped lang="scss">
</style>