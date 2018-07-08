<template>
  <div class="card" :key="card.id">
    <CardTitle :title="card.name"/>
    <CardImgBig :imgUrl="card.imgUrl"/>
  </div>
</template>

<script>
import CardTitle from './CardTitle'
import CardImgBig from './CardImgBig'

export default {
  name: 'Card',
  props: {
    card: Object
  },
  components : {
      CardTitle,
      CardImgBig
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
    display: inline-block
  }
</style>
