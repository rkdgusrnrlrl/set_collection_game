<template>
    <div class="hand" style="display: block">
        <Card v-for="card in cards"
                         :card="card"
                         :key="card.id"></Card>
    </div>
</template>

<script>
    import Card from './Card'


    export default {
        name: "MyHand",
        props: ['cards'],
        components : {
            Card
        }
    }
</script>

<style scoped>

</style>