<template>
    <header class="d-flex align-items-center justify-content-between">
        <nav class="d-flex align-items-center">
            <h2>BOOLFLIX</h2>

            <ul>
                <li @click.prevent="goHome">Home</li>
            </ul>

        </nav>
        <div class="input-group mb-3 search">
            <span class="input-group-text" id="button-search" @click.prevent="goSearch">
                <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
            </span>
            <input type="text" class="form-control" id="my-input" @keyup.enter="goSearch" v-model="userSearch">
            <select class="form-select " id="my-select" aria-label="Default select example" v-model="typeSearch">
                <option value="">All</option>
                <option value="film">Film</option>
                <option value="serie">Serie</option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderVue',
    data() {
        return {
            userSearch: '',
            typeSearch: '',
            home: false
        }
    },
    methods: {
        goSearch() {
            this.home = false;
            this.sendInputUser();
        },
        goHome() {
            this.home = true;
            this.userSearch = '';
            this.sendInputUser();
        },
        sendInputUser() {
            this.$emit('myInput', { type: this.typeSearch, text: this.userSearch, home: this.home });
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
    right: 0;
    left: 0;
    top: 0;
    z-index: 100;

    nav {

        h2 {
            color: #e50914;
            margin: 0;
        }

        ul {
            display: inline-block;
            margin: 0;

            li {
                list-style-type: none;
                color: white;

                &:hover {
                    cursor: pointer;
                }
            }
        }
    }

    .search {
        max-width: 350px;
        margin: 0 !important;

        #button-search:hover {
            cursor: pointer;
        }

        #my-input {
            width: 200px;
            color: #242424;
        }

        #my-select {
            border-radius: 0 5px 5px 0;
            background-color: white;
            color: #242424;
            width: 75px;
            display: block;
        }
    }
}
</style>
