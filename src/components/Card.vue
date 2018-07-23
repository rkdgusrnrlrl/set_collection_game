<template>
    <drag class="card" :key="card.id" :style="position"
          :transfer-data="{ item: card, list: parent}">

        <CardTitle v-if="card.state == 'front'" :title="card.name"/>
        <CardImgBig v-if="card.state == 'front'" :imgUrl="card.imgUrl"/>

    </drag>
</template>

<script>
    import CardTitle from './CardTitle'
    import CardImgBig from './CardImgBig'
    import {Drag, Drop} from 'vue-drag-drop'

    export default {
        name: 'Card',
        props: {
            card: Object,
            index : Number,
            position : Object,
            parent : Array
        },
        components : {
            CardTitle,
            CardImgBig,
            Drag,
            Drop
        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .card {
    padding: 8px;
    margin-left: 8px;
    margin-bottom: 8px;
    width: 150px;
    height: 190px;
    background-color: cornflowerblue;
    border: 1px solid black;
  }
</style>
