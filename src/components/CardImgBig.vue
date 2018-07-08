<template>
    <div class="card_img_big">
        {{ imgUrl }}
    </div>
</template>

<script>
    export default {
        name: "card-img-big",
        props: {
            'imgUrl' : String
        }
    }
</script>

<style scoped>
    .card_img_big {
        width: 100%;
        height: 80%;
        background-color: aliceblue;
    }
</style>