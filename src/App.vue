<template>
  <div id="app">
      <MyHand :cards="players[1].hand" :player="players[1]"/>
      <div style="display: flex; flex-direction: row">
          <CardCol v-for="flag in players[1].flags"
                   :cards="flag"
                   :player="players[1]"/>
      </div>
      <div style="display: flex; flex-direction: row">
          <Card :card="{name : '1 flag'}" style="margin: 9px"/>
          <Card :card="{name : '2 flag'}" style="margin: 9px"/>
          <Card :card="{name : '3 flag'}" style="margin: 9px"/>
          <Card :card="{name : '4 flag'}" style="margin: 9px"/>
      </div>
      <div style="display: flex; flex-direction: row">
          <CardCol v-for="flag in players[0].flags"
                   :cards="flag"
                   :player="players[0]"/>
      </div>

      <div style="display: flex; flex-direction: row; margin-top: 20px;">
          <CardDumy :cardSpace="currentPlayer.hand" :cardDumy="dumy" :player="currentPlayer"/>
          <MyHand :cards="players[0].hand" :player="players[0]"/>
      </div>
      <button @click="turnEnd(players[0])">자신 턴종료</button>
      <button @click="turnEnd(players[1])">상대방 턴종료</button>
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
          game : {
              turn : 0
          },
          currentPlayer : {},
          players : [
              {
                  id : "first",
                  isDraw : false,
                  action : 2,
                  state : "READY",
                  hand : [],
                  flags : [
                      [],
                      [],
                      [],
                      []
                  ]
              },
              {
                  id : "second",
                  isDraw : true,
                  action : 0,
                  state : "DONE",
                  hand : [],
                  flags : [
                      [],
                      [],
                      [],
                      []
                  ]
              }
          ],
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
    },
    created () {
        this.currentPlayer = this.players[0];

        this.$on('turnStart', (player) => {
            if (player.id === this.players[0].id) {
                alert(`이제 당신 턴입니다.`)
            }
        })

        this.$on('turnEnd', (player) => {
            player.state = "DONE"
            const playerIdx = _.findIndex(this.players, (p) => p.id === player.id)

            let nextPlayerIdx = 0;
            if (playerIdx + 1 < this.players.length) {
                nextPlayerIdx = playerIdx + 1
            }

            this.players[nextPlayerIdx].state = "READY"
            this.players[nextPlayerIdx].isDraw = false
            this.players[nextPlayerIdx].action = 2
            this.currentPlayer = this.players[nextPlayerIdx]

            this.$emit('turnStart', this.players[nextPlayerIdx])
        })
    },
    methods : {
        turnEnd(player) {
            if (player.state !== "READY") {
                alert("다른 사람 턴입니다.")
                return
            }

            const isOk = confirm("턴을 종료 하시겠습니까??")
            if (isOk) {
                this.$emit('turnEnd', player)
            }
        }
    }

}
</script>

<style>

</style>
