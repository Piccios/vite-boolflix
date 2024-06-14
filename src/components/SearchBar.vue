<script>
    export default {
        data() {
            return {
                query: ''
            };
        },
        methods: {
            search() {
                this.$emit('search', this.query);
            }
        }
    };
</script>

<template>
    <div>
        <input v-model="query" @keyup.enter="search" placeholder="Cerca un film..."/>
        <button @click="search">Cerca</button>
    </div>
</template>