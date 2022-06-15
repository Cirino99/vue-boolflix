<template>
    <header class="d-flex align-items-center justify-content-between">
        <h3>BOOLFLIX</h3>
        <div>
            <input type="text" v-model="userSearch" @keyup.enter="sendInputUser">
            <button @click.prevent="sendInputUser">Search</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderVue',
    data() {
        return {
            userSearch: ''
        }
    },
    methods: {
        sendInputUser() {
            this.$emit('myInput', this.userSearch);
        }
    }
}
</script>

<style scoped lang="scss">
header {
    background-color: #000000;
    height: 70px;
    padding: 0 20px;

    h3 {
        color: #e50914;
    }
}
</style>
