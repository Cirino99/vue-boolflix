<template>
    <div id="app">
        <HeaderVue @myInput="searchData" />
        <main>
            <SearchFilmVue v-if="search" :films="listMovies" :series="listSeries" />
            <HomeVue v-else :popularFilms="listPopularMovie" :topFilms="listTopMovie" :popularSeries="listPopularSerie"
                :topSeries="listTopSerie" />
        </main>
    </div>
</template>

<script>
import HeaderVue from './components/Header.vue';
import SearchFilmVue from './components/SearchFilm.vue';
import axios from 'axios';
import HomeVue from './components/Home.vue';

export default {
    name: 'App',
    components: {
        HeaderVue,
        SearchFilmVue,
        HomeVue
    },
    data() {
        return {
            urlApi: {
                urlMovie: 'https://api.themoviedb.org/3/search/movie?',
                urlSeries: 'https://api.themoviedb.org/3/search/tv?',
                urlPopularMovie: 'https://api.themoviedb.org/3/movie/popular?',
                urlTopMovie: 'https://api.themoviedb.org/3/movie/top_rated?',
                urlPopularSerie: 'https://api.themoviedb.org/3/tv/popular?',
                urlTopSerie: 'https://api.themoviedb.org/3/tv/top_rated?',
                key: '049b0824b24d9a73de8047a8a18e7c77',
                language: 'it-IT',
            },
            listMovies: [],
            listSeries: [],
            listPopularMovie: [],
            listTopMovie: [],
            listPopularSerie: [],
            listTopSerie: [],
            search: false
        }
    },
    created() {
        this.getHome();
    },
    methods: {
        searchData(userData) {
            this.search = true;
            this.listMovies = [];
            this.listSeries = [];
            if (userData[0] === '') {
                this.axiosFunction(this.urlApi.urlMovie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + userData[1], 'movie');
                this.axiosFunction(this.urlApi.urlSeries + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + userData[1], 'serie');
            } else if (userData[0] === 'film') {
                this.axiosFunction(this.urlApi.urlMovie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + userData[1], 'movie');
            } else {
                this.axiosFunction(this.urlApi.urlSeries + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language + '&query=' + userData[1], 'serie');
            }
        },
        axiosFunction(url, type) {
            axios.get(url).then((result) => {
                switch (type) {
                    case 'movie':
                        this.listMovies = result.data.results;
                        break;
                    case 'serie':
                        this.listSeries = result.data.results;
                        break;
                    case 'popularMovie':
                        this.listPopularMovie = this.cutArray(result.data.results, 5);
                        break;
                    case 'topMovie':
                        this.listTopMovie = this.cutArray(result.data.results, 5);
                        break;
                    case 'popularSerie':
                        this.listPopularSerie = this.cutArray(result.data.results, 5);
                        break;
                    case 'topSerie':
                        this.listTopSerie = this.cutArray(result.data.results, 5);
                        break;
                }
            }).catch((error) => {
                console.log('Errore', error);
            });
        },
        getHome() {
            this.search = false;
            this.axiosFunction(this.urlApi.urlPopularMovie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language, 'popularMovie');
            this.axiosFunction(this.urlApi.urlTopMovie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language, 'topMovie');
            this.axiosFunction(this.urlApi.urlPopularSerie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language, 'popularSerie');
            this.axiosFunction(this.urlApi.urlTopSerie + 'api_key=' + this.urlApi.key + '&language=' + this.urlApi.language, 'topSerie');
        },
        cutArray(arr, length) {
            let arr2 = [];
            for (let i = 0; i < length; i++) {
                arr2.push(arr[i]);
            }
            return arr2;
        }
    },
}
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap.scss";

* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100%;
    height: 100vh;
    overflow-y: scroll;
    background-color: #434343;
    position: relative;
}
</style>
