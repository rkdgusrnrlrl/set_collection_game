<template>
    <div class="card" @click="drawCardTo()"/>
</template>

<script>
    export default {
        name: "CardDumy",
        props : {
            cardSpace : Array,
            cardDumy : Array,
            player : Object
        },
        methods : {
            drawCardTo() {
                if (this.player.state === "DONE") {
                    alert("다른 플레이어 턴입니다.")
                } else if (this.player.isDraw) {
                    alert("이미 드로우 했습니다.")
                } else {
                    while (this.cardSpace.length < 5) {
                        this.cardSpace.push(this.cardDumy.pop())
                    }
                    this.player.isDraw = true;
                }
            }
        }
    }
</script>

<style scoped>
    .card {
        padding: 8px;
        margin-left: 8px;
        margin-right: 8px;
        margin-bottom: 8px;
        width: 150px;
        height: 190px;
        background-color: cornflowerblue;
        border: 1px solid black;
    }
</style>