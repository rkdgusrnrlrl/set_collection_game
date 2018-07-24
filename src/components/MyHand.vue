<template>
    <drop class="card_row noselect" @drop="drop(cards, ...arguments)">
        <Card v-for="card in cards"
            :parent="cards"
            :card="card"
            :key="card.id"
            :isMyTurn="isDraggable()"
        />
    </drop>
</template>

<script>
    import Card from './Card'
    import {Drag, Drop} from 'vue-drag-drop'


    export default {
        name: "MyHand",
        props: ['cards', 'player'],
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
            },
            isDraggable() {
                return this.player.state === "READY"
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
.noselect {
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
    -khtml-user-select: none; /* Konqueror HTML */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
}
</style>