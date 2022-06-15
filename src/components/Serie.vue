<template>
    <div @mouseover="cardHover = true" @mouseleave="cardHover = false">
        <img v-if="serie.poster_path !== null" :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path" alt="">
        <div v-else class="copertina d-flex justify-content-center align-items-center">
            <h2>{{ serie.name }}</h2>
        </div>
        <div class="description d-flex flex-column" :class="!cardHover ? 'd-none' : ''">
            <span> <strong>Titolo: </strong>{{ serie.name }}</span>
            <span> <strong>Titolo originale:</strong> {{ serie.original_name }}</span>

            <span>
                <strong>Voto: </strong>
                <font-awesome-icon icon="fa-solid fa-star" v-for="(star, index) in ratingStar" :key="index" />
                <font-awesome-icon icon="fa-regular fa-star" v-for="(star, index) in (5 - ratingStar)"
                    :key="index + ratingStar" />
            </span>
            <span><strong>Lingua originale:</strong>
                <lang-flag :iso="serie.original_language" />
            </span>
            <span><strong>Trama:</strong> {{ overviewSerie }}</span>
            <span>serie</span>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'SerieVue',
    components: {
        LangFlag
    },
    props: {
        serie: Object
    },
    data() {
        return {
            cardHover: false
        }
    },
    computed: {
        ratingStar() {
            return Math.ceil(this.serie.vote_average / 2);
        },
        overviewSerie() {
            return this.serie.overview.substr(0, 350) + '...';
        }
    }
}
</script>

<style scoped lang="scss">
div {
    background-color: #000000;
    position: relative;
    padding: 10px;

    .description {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        color: white;
        padding-top: 60px;
    }

    .copertina {
        width: 342px;
        height: 513px;
        color: white;
    }
}
</style>