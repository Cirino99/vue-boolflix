<template>
    <div id="app">
        <HeaderVue />
        <MainVue />
    </div>
</template>

<script>
import HeaderVue from './components/Header.vue';
import MainVue from './components/Main.vue';
//import axios from 'axios';

export default {
    name: 'App',
    components: {
        HeaderVue,
        MainVue
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
