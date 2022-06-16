<template>
    <section>
        <h2>Film popolari</h2>
        <div class="d-flex flex-wrap">
            <CardFilmVue v-for="(card) in filmPopular" :key="card.id" :item="card" />
        </div>
        <h2>Top film</h2>
        <div class="d-flex flex-wrap">
            <CardFilmVue v-for="(card) in filmTop" :key="card.id" :item="card" />
        </div>
        <h2>Serie popolari</h2>
        <div class="d-flex flex-wrap">
            <CardFilmVue v-for="(card) in seriePopular" :key="card.id" :item="card" />
        </div>
        <h2>Top serie</h2>
        <div class="d-flex flex-wrap">
            <CardFilmVue v-for="(card) in serieTop" :key="card.id" :item="card" />
        </div>
    </section>
</template>

<script>
import CardFilmVue from './CardFilm.vue';
export default {
    name: "HomeVue",
    components: { CardFilmVue },
    props: {
        popularFilms: Array,
        topFilms: Array,
        popularSeries: Array,
        topSeries: Array
    },
    computed: {
        filmPopular() {
            let arr = [];
            this.popularFilms.forEach(element => {
                arr.push({
                    nome: element.title,
                    nomeOriginale: element.original_title,
                    poster: element.poster_path,
                    voto: element.vote_average,
                    lingua: element.original_language,
                    trama: element.overview,
                    id: element.id,
                    categoria: 'film'
                });
            });
            return arr
        },
        filmTop() {
            let arr = [];
            this.topFilms.forEach(element => {
                arr.push({
                    nome: element.title,
                    nomeOriginale: element.original_title,
                    poster: element.poster_path,
                    voto: element.vote_average,
                    lingua: element.original_language,
                    trama: element.overview,
                    id: element.id,
                    categoria: 'film'
                });
            });
            return arr
        },
        seriePopular() {
            let arr = [];
            this.popularSeries.forEach(element => {
                arr.push({
                    nome: element.name,
                    nomeOriginale: element.original_name,
                    poster: element.poster_path,
                    voto: element.vote_average,
                    lingua: element.original_language,
                    trama: element.overview,
                    id: element.id,
                    categoria: 'serie'
                });
            });
            return arr
        },
        serieTop() {
            let arr = [];
            this.topSeries.forEach(element => {
                arr.push({
                    nome: element.name,
                    nomeOriginale: element.original_name,
                    poster: element.poster_path,
                    voto: element.vote_average,
                    lingua: element.original_language,
                    trama: element.overview,
                    id: element.id,
                    categoria: 'serie'
                });
            });
            return arr
        }
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
}
</style> 