<template>
  <div id="list-games">
    <ul>
      <li v-for="game in games">
        <h2>{{ game.name }}</h2>
        <h3>{{ game.platform }}</h3>
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  props: {
  games: {
    type: Array,
    required: true
  }
},
  data () {
    return {
    }
  },
  methods:{
  }
}
</script>

<style scoped>
#list-games{
    width: 100%;
    max-width: 1200px;
    margin: 40px auto;
    padding: 0 20px;
    box-sizing: border-box;
}
ul{
    display: flex;
    flex-wrap: wrap;
    list-style-type: none;
    padding: 0;
}
li{
    flex-grow: 1;
    flex-basis: 300px;
    text-align: center;
    padding: 30px;
    border: 1px solid #222;
    margin: 10px;
}
</style>
