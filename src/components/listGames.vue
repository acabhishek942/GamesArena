<template>
  <div id="list-games">
    <ul>
      <li v-for="game in games">
        <h2>{{ game.title }}</h2>
        <!-- Display platform and score only on click -->
          <button v-on:click="showGameDetails(game)">Show Details</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { bus } from '../main';
export default {
  props: {
  },
  data () {
    return {
      games: []
    }
  },
  methods:{
    showGameDetails: function(game){
      bus.$emit('show-game-detail-modal', game)
    }
  },
  created(){
    // refer https://youtu.be/ieCsEdq94TA?list=PL4cUxeGkcC9gQcYgjhBoeQH7wiAyZNrYa&t=575
    // to understand this lifecycke hook.
    this.$http.get('http://starlord.hackerearth.com/gamesext').then(function(data){
      return data.json();
    }).then(function(data){
      var gamesArray = [];
      // below three lines add the property 'show' to all the objects in gamesArray
      for (let key in data){
        data[key].show = false;
        gamesArray.push(data[key]);
      }
      this.games = gamesArray.slice(20, 30);
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
