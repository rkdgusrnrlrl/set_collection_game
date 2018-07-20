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

    export default {
        name: "CardCol",
        props: ['cards'],
        components : {
            Card,
            Drop,
            Drag
        },
        methods : {
            drop(toList, data) {
                const fromList = data.list;
                if (fromList) {
                    toList.push(data.item);
                    fromList.splice(fromList.indexOf(data.item), 1);
                    toList.sort((a, b) => a > b);
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