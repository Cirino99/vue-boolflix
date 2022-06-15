<template>
    <header>
        <input type="text" v-model="userSearch" @keyup.enter="sendInputUser">
        <button @click.prevent="sendInputUser">Search</button>
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
</style>
