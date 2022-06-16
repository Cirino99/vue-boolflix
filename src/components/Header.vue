<template>
    <header class="d-flex align-items-center justify-content-between">
        <h3>BOOLFLIX</h3>
        <div>
            <input type="text" v-model="userSearch" @keyup.enter="sendInputUser">
            <select name="type" v-model="typeSearch">
                <option value="">All</option>
                <option value="film">Film</option>
                <option value="serie">Serie</option>
            </select>
            <button @click.prevent="sendInputUser">Search</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderVue',
    data() {
        return {
            userSearch: '',
            typeSearch: ''
        }
    },
    methods: {
        sendInputUser() {
            console.log(this.typeSearch);
            this.$emit('myInput', [this.typeSearch, this.userSearch]);
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
