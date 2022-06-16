<template>
    <header class="d-flex align-items-center justify-content-between">
        <nav class="d-flex align-items-center">
            <h2>BOOLFLIX</h2>

            <ul>
                <li @click.prevent="goHome"><a href="#">Home</a></li>
            </ul>

        </nav>
        <div class="search">
            <input type="text" v-model="userSearch" @keyup.enter="goSearch">
            <select name="type" v-model="typeSearch">
                <option value="">All</option>
                <option value="film">Film</option>
                <option value="serie">Serie</option>
            </select>
            <button @click.prevent="goSearch">
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

                a {
                    color: white;
                    text-decoration: none;
                }

            }
        }
    }

    .search {
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
            padding: 0 5px;
        }
    }
}
</style>
