<template>
    <div>
        <span>{{ film.title }}</span>
        <span>{{ film.original_title }}</span>
        <span>{{ film.original_language }}</span>
        <span>{{ film.vote_average }}</span>
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
</style>