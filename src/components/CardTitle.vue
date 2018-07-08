<template>
    <div class="card_til">{{ title }}</div>
</template>

<script>
    export default {
        name: "card-title",
        props: {
            'title' : String
        }
    }
</script>

<style scoped>
    .card_til {
        margin-bottom: 10%;
        width: 100%;
        height: 10%;
        background-color: aliceblue;
    }
</style>