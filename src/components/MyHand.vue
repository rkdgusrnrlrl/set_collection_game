<template>
    <drop class="card_row" @drop="drop(cards, ...arguments)">
        <Card v-for="card in cards"
            :parent="cards"
            :card="card"
            :key="card.id"/>
    </drop>
</template>

<script>
    import Card from './Card'
    import {Drag, Drop} from 'vue-drag-drop'


    export default {
        name: "MyHand",
        props: ['cards'],
        components : {
            Card,
            Drag,
            Drop
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
.card_row {
    display: flex;
    flex-direction: row;
    flex-wrap : wrap;
}
</style>