<template>
    <div class="card" @mouseover="cardHover = true" @mouseleave="cardHover = false">
        <img v-if="item.poster !== null" :src="'https://image.tmdb.org/t/p/w342' + item.poster" :alt="item.nome">
        <div v-else class="copertina d-flex justify-content-center align-items-center">
            <h2>{{ item.nome }}</h2>
        </div>
        <div class="description d-flex flex-column" :class="!cardHover ? 'd-none' : ''">
            <span> <strong>Titolo: </strong>{{ item.nome }}</span>
            <span> <strong>Titolo originale:</strong> {{ item.nomeOriginale }}</span>

            <span>
                <strong>Voto: </strong>
                <font-awesome-icon class="star-icon" icon="fa-solid fa-star" v-for="(star, index) in ratingStar"
                    :key="index" />
                <font-awesome-icon class="star-icon" icon="fa-regular fa-star" v-for="(star, index) in (5 - ratingStar)"
                    :key="index + ratingStar" />
            </span>
            <span><strong>Lingua originale:</strong>
                <lang-flag :iso="item.lingua" />
            </span>
            <span><strong>Categoria: </strong>{{ item.categoria }}</span>
            <span><strong>Trama:</strong> {{ overviewItem }}</span>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'CardVue',
    components: {
        LangFlag
    },
    props: {
        item: Object
    },
    data() {
        return {
            cardHover: false
        }
    },
    computed: {
        ratingStar() {
            return Math.ceil(this.item.voto / 2);
        },
        overviewItem() {
            return this.item.trama.substr(0, 350) + '...';
        }
    }
}
</script>

<style scoped lang="scss">
.card {
    background-color: #000000;
    position: relative;
    border-radius: 0;
    margin: 10px;

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