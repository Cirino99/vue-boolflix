<template>
    <div id="app">
        <HeaderVue @myInput="searchData" />
        <main>
            <SearchFilmVue v-if="listFilms !== ''" :listFilms="listFilms" />
        </main>
    </div>
</template>

<script>
import HeaderVue from './components/Header.vue';
import SearchFilmVue from './components/SearchFilm.vue';
import axios from 'axios';

export default {
    name: 'App',
    components: {
        HeaderVue,
        SearchFilmVue
    },
    data() {
        return {
            urlApi: {
                urlMovie: 'https://api.themoviedb.org/3/search/movie?',
                urlSeries: 'https://api.themoviedb.org/3/search/tv?',
                key: '049b0824b24d9a73de8047a8a18e7c77',
                language: 'it-IT',
            },
            listFilms: ''
        }
    },
    methods: {
        searchData(e) {
            console.log(this.urlApi.urlMovie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + e);
            axios.get(this.urlApi.urlMovie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + e).then((result) => {
                this.listFilms = result.data.results;
            }).catch((error) => {
                console.log('Errore', error);
            });
        }
    }
}
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap.scss";

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
</style>
