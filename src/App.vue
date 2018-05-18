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
        {name: 'God of War', platform: 'Mac OSX', show: false},
        {name: 'Crazy Taxi', platform: 'Windows', show: false},
        {name: 'GTA 5', platform: 'Windows', show: false},
        {name: 'Tekken', platform: 'Windows', show: false},
        {name: 'Pocket Tanks', platform: 'Android/Windows', show: false},
        {name: 'Kwazy Cupcskes', platform: 'Android', show: false}
      ]
    }
  },
  methods:{
  }
}
</script>

<style>
</style>
