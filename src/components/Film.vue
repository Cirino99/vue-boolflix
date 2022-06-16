<template>
    <div class="card" @mouseover="cardHover = true" @mouseleave="cardHover = false">
        <img v-if="film.poster_path !== null" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" alt="">
        <div v-else class="copertina d-flex justify-content-center align-items-center">
            <h2>{{ film.title }}</h2>
        </div>
        <div class="description d-flex flex-column" :class="!cardHover ? 'd-none' : ''">
            <span> <strong>Titolo: </strong>{{ film.title }}</span>
            <span> <strong>Titolo originale:</strong> {{ film.original_title }}</span>

            <span>
                <strong>Voto: </strong>
                <font-awesome-icon class="star-icon" icon="fa-solid fa-star" v-for="(star, index) in ratingStar"
                    :key="index" />
                <font-awesome-icon class="star-icon" icon="fa-regular fa-star" v-for="(star, index) in (5 - ratingStar)"
                    :key="index + ratingStar" />
            </span>
            <span><strong>Lingua originale:</strong>
                <lang-flag :iso="film.original_language" />
            </span>
            <span><strong>Categoria: </strong>film</span>
            <span><strong>Trama:</strong> {{ overviewFilm }}</span>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'FilmVue',
    components: {
        LangFlag
    },
    props: {
        film: Object
    },
    data() {
        return {
            cardHover: false
        }
    },
    computed: {
        ratingStar() {
            return Math.ceil(this.film.vote_average / 2);
        },
        overviewFilm() {
            return this.film.overview.substr(0, 350) + '...';
        }
    }
}
</script>

<style scoped lang="scss">
.card {
    background-color: #000000;
    position: relative;
    padding: 10px;
    border: solid .5px white;
    border-radius: 0;

    .description {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        color: white;
        padding: 10px;
        padding-top: 60px;
        background-color: #000000;

        .star-icon {
            color: gold;
        }
    }

    .copertina {
        width: 342px;
        height: 513px;
        color: white;
    }
}
</style>