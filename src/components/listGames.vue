<template>
  <div id="list-games">
    <ul>
      <li v-for="game in games" v-on:click="game.show = !game.show">
        <h2>{{ game.title }}</h2>
        <div v-show="game.show">
          <h3>Platform : {{ game.platform }}</h3>
          <h3>High Score : {{ game.highScore }}</h3>
        </div>
      </li>
    </ul>

  </div>
</template>

<script>
import Vue from 'vue'
export default {
  props: {
  },
  data () {
    return {
      games: []
    }
  },
  methods:{
  },
  created(){
    this.$http.get('http://starlord.hackerearth.com/gamesext').then(function(data){
      console.log(data);
      this.games = data.body.slice(11, 20);
      console.log(this.games);
    });
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
