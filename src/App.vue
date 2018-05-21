<template>
  <div>
    <app-header v-bind:title="title"></app-header>
    <list-games v-bind:games="games"></list-games>
    <app-footer v-bind:title="title"></app-footer>
  </div>
</template>

<script>

import listGames from './components/listGames.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
export default {
  components:{
    'list-games': listGames,
    'app-header': Header,
    'app-footer': Footer,
  },
  data () {
    return {
      title: 'Games Arena',
      games: [
        {name: 'God of War', platform: 'Mac OSX', highScore: 23, show: false},
        {name: 'Crazy Taxi', platform: 'Windows', highScore: 23, show: false},
        {name: 'GTA 5', platform: 'Windows', highScore: 23, show: false},
        {name: 'Tekken', platform: 'Windows', highScore: 23, show: false},
        {name: 'Pocket Tanks', platform: 'Android/Windows', highScore: 23, show: false},
        {name: 'Kwazy Cupcskes', platform: 'Android', highScore: 23, show: false},
        {name: 'Far Cry 1', platform: 'Windows', highScore: 23, show: false},
        {name: 'Far Cry 2', platform: 'Windows', highScore: 23, show: false},
        {name: 'Far Cry 3', platform: 'Windows', highScore: 23, show: false},
        {name: 'Far Cry 4', platform: 'Windows', highScore: 23, show: false},
        {name: 'Far Cry 5', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 11', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 12', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 13', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 14', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 15', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 16', platform: 'Windows', highScore: 23, show: false},
        {name: 'EA FIFA 17', platform: 'Windows', highScore: 23, show: false},
      ]
    }
  },
  methods:{
  },
}
</script>

<style>
</style>
