<template>
    <div id="app">
        <HeaderVue @myInput="searchData" />
        <MainVue v-if="listFilms !== ''" :listFilms="listFilms" />
    </div>
</template>

<script>
import HeaderVue from './components/Header.vue';
import MainVue from './components/Main.vue';
import axios from 'axios';

export default {
    name: 'App',
    components: {
        HeaderVue,
        MainVue
    },
    data() {
        return {
            urlApi: 'https://api.themoviedb.org/3/search/movie?api_key=049b0824b24d9a73de8047a8a18e7c77&language=it-IT&query=',
            listFilms: ''
        }
    },
    methods: {
        searchData(e) {
            console.log(this.urlApi + e);
            axios.get(this.urlApi + e).then((result) => {
                console.log(result.data.results);
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
