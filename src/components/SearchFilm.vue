<template>
    <section>
        <h2>Risultati della ricerca:</h2>
        <div class="d-flex flex-wrap">
            <CardFilmVue v-for="(card) in generalList" :key="card.id" :item="card" />
        </div>
    </section>
</template>

<script>
import CardFilmVue from './CardFilm.vue';
export default {
    name: "SearchFilmVue",
    components: { CardFilmVue },
    props: {
        films: Array,
        series: Array
    },
    computed: {
        generalList() {
            let arr = [];
            this.films.forEach(element => {
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
            this.series.forEach(element => {
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
            console.log(arr);
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
    }
}
</style>