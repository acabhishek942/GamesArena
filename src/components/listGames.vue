<template>
  <div id="list-games">
    <input type="text" v-model="search" placeholder="search games" />
    <ul>
      <li v-for="game in filteredGames">
        <h2>{{ game.title }}</h2>
        <!-- A button which opens the modal that displays the game details -->
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
      games: [],
      search: '',
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
      this.games = gamesArray.slice(20, 37);
    });
  },
  computed: {
    filteredGames: function() {
      return this.games.filter((game) => {
        return game.title.toLowerCase().match(this.search.toLowerCase());
      })
    }
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

input {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    margin: 40px;
}
</style>
