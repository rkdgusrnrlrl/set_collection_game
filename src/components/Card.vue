<template>
    <drag class="card" :key="card.id" :style="position"
          :draggable="isMyTurn"
          :transfer-data="{ item: card, list: parent}">

        <CardTitle class="noselect" v-if="card.state == 'front'" :title="card.name"/>
        <CardImgBig class="noselect" v-if="card.state == 'front'" :imgUrl="card.imgUrl"/>

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
            parent : Array,
            isMyTurn : Boolean

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
