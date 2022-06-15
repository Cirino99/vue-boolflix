<template>
    <div id="app">
        <HeaderVue @myInput="searchData" />
        <main>
            <SearchFilmVue v-if="listMovies !== '' || listSeries !== ''" :films="listMovies" :series="listSeries" />
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
            listMovies: [],
            listSeries: []
        }
    },
    methods: {
        searchData(userData) {
            this.axiosFunction(this.urlApi.urlMovie, userData, 'movie');
            this.axiosFunction(this.urlApi.urlSeries, userData, 'serie');
        },
        axiosFunction(url, query, type) {
            console.log(url + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + query);
            axios.get(url + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + query).then((result) => {
                if (type === 'movie') {
                    this.listMovies = result.data.results;
                } else {
                    this.listSeries = result.data.results;
                }

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
    width: 100%;
    height: 100vh;
    overflow: auto;
    background-color: #434343;
}
</style>
