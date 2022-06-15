<template>
    <div class="d-flex flex-column align-items-center col-2 text-center">
        <h3>Titolo: {{ film.title }}</h3>
        <h4>Titolo originale: {{ film.original_title }}</h4>
        <span>Lingua originale: {{ film.original_language }}</span>
        <span>Voto: {{ film.vote_average }}</span>
    </div>
</template>

<script>
export default {
    name: 'FilmVue',
    props: {
        film: Object
    }
}
</script>

<style scoped lang="scss">
div {
    background-color: aqua;
    border-radius: 20px;
}
</style>