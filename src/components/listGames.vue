<template>
  <div id="list-games">
    <ul>
      <li v-for="game in games" v-on:click="game.show = !game.show">
        <h2>{{ game.name }}</h2>
        <div v-show="game.show">
          <h3>Platform : {{ game.platform }}</h3>
          <h3>High Score : {{ game.highScore }}</h3>
        </div>
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
    padding: 50px 20px;
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
