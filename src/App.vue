<template>
  <div id="app">
      <!--
    <Card :card="card"/>

    <MyHand :cards="cards"/>
    <CardCol :cards="cardrs"/>

    <MyHand :cards="cards"/>
    <CardCol :cards="region1"/>
    -->

      <CardDumy :cardSpace="myhand" :cardDumy="dumy"/>
      <MyHand :cards="myhand"/>

      <div style="display: flex; flex-direction: row">
          <CardCol :cards="region1"/>
          <CardCol :cards="region2"/>
          <CardCol :cards="region3"/>
          <CardCol :cards="region4"/>
      </div>
  </div>
</template>

<script>
import Card from './components/Card'
import CardDumy from './components/CardDumy'
import MyHand from './components/MyHand'
import CardCol from './components/CardCol'
import draggable from 'vuedraggable'
import _ from 'lodash'

const CARD_COLORS = ["Red", "Greeon", "Orange", "Puple", "Blue", "Yellow"];
let fullCardDumy = []
for (let i = 0; i < CARD_COLORS.length; i++) {
    for (let j = 1; j < 11; j++) {
        fullCardDumy.push({
            id : CARD_COLORS[i]+j,
            color : CARD_COLORS[i], number : j,
            name : `${CARD_COLORS[i]} ${j}`,
            imgUrl : `${CARD_COLORS[i]} ${j}`,
            state : "front"
        })
    }
}
fullCardDumy =_.shuffle(fullCardDumy)


export default {
  name: 'app',
  components: {
    Card,
    CardDumy,
    MyHand,
    CardCol,
    draggable
  },
  data() {
      return {
          cards : [
              {name:"Joao", id:6, imgUrl : "img"},
              {name:"Joao", id:7, imgUrl : "img"},
              {name:"Joao", id:8, imgUrl : "img"}
          ],
          cardrs : [
              {name:"Red 1", id:9, imgUrl : "img"},
              {name:"Red 2", id:10, imgUrl : "img"},
              {name:"Red 3", id:11, imgUrl : "img"}
          ],
          card : {name:"Joao", id:2, imgUrl : "img"},
          list1:[{name:"John", id:1},
              {name:"Joao", id:3},
              {name:"Jean", id:4},
              {name:"Gerard", id:5} ],
          list2 : [
              {name:"qJoao", id:2},
          ],
          dumy : fullCardDumy,
          myhand : [],
          region1 : [],
          region2 : [],
          region3 : [],
          region4 : []
      }
  }
}
</script>

<style>

</style>
