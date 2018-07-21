<template>
    <drop class="card_col" style="border: 1px solid black" @drop="drop(cards, ...arguments)">
        <Card v-for="(card, index) in cards"
            :position="{position: 'absolute', display: 'block', zIndex : index, top : index * 40 + 'px'}"
            :parent="cards"
            :card="card"
            :index="index"
            :key="card.id"></Card>
    </drop>
</template>

<script>
    import Card from './Card'
    import {Drag, Drop} from 'vue-drag-drop'
    import _ from 'lodash'

    export default {
        name: "CardCol",
        props: {
            cards : Array,
            player : Object
        },
        components : {
            Card,
            Drop,
            Drag
        },
        methods : {
            drop(toList, data) {
                const fromList = data.list;

                let state = prompt("카드 상태?")

                if (fromList) {
                    //앞 : front, 뒤 back
                    if (state === "front") {
                        if (this.player.action >= 1) {
                            const card = _.assignIn({}, data.item, {state});
                            toList.push(card);
                            fromList.splice(fromList.indexOf(data.item), 1);
                            toList.sort((a, b) => a > b);
                            this.player.action -= 1
                        } else {
                            alert(`남은 액션이 부족합니다.(남은 액션 : ${this.player.action})`)
                        }
                    } else if (state === "back") {
                        if (this.player.action >= 2) {
                            const card = _.assignIn({}, data.item, {state});
                            toList.push(card);
                            fromList.splice(fromList.indexOf(data.item), 1);
                            toList.sort((a, b) => a > b);
                            this.player.action -= 2
                        } else {
                            alert(`남은 액션이 부족합니다.(남은 액션 : ${this.player.action})`)
                        }
                    }
                }
            }
        }
    }
</script>

<style scoped>
    .card_col {
        position: relative;
        display: flex;
        flex-direction: column;
        width : 185px;
        min-height: 300px;
        height: 100%;
        border: 1px solid black;
    }
</style>