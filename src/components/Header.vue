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
            <button @click.prevent="sendInputUser">
                <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
            </button>
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
            this.userSearch = this.userSearch.trim();
            if (this.userSearch !== '')
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
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    width: 100%;

    h3 {
        color: #e50914;
    }

    div {
        input {
            border-radius: 5px 0 0 5px;
            height: 35px;
            background-color: white;
            color: #242424;
        }

        select {
            height: 35px;
            border-radius: 0;
            background-color: white;
            color: #242424;
        }

        button {
            height: 35px;
            border-radius: 0 5px 5px 0;
            background-color: white;
            color: #242424;
        }
    }
}
</style>
