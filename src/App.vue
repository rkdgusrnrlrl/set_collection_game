<template>
  <div id="app">
    <Card :card="card"/>
    <draggable element="ul" class="dragArea" :list="list1" :options="{group:'people'}" style="border: 1px solid black">
      <li v-for="(element, index) in list1" :key="element.id">
        {{element.name}} {{index}}
      </li>
    </draggable>

    <draggable element="ul" class="dragArea" :list="list2" :options="{group:'people'}" style="border: 1px solid black">
      <li v-for="(element, index) in list2" :key="element.id">
        {{element.name}} {{index}}
      </li>
    </draggable>
  </div>
</template>

<script>
import Card from './components/Card.vue'
import draggable from 'vuedraggable'

export default {
  name: 'app',
  components: {
    Card,
    draggable
  },
  data() {
      return {
          card : {name:"Joao", id:2, imgUrl : "img"},
          list1:[{name:"John", id:1},
              {name:"Joao", id:3},
              {name:"Jean", id:4},
              {name:"Gerard", id:5} ],
          list2 : [
              {name:"qJoao", id:2},
          ]
      }
  }
}
</script>

<style>

</style>
