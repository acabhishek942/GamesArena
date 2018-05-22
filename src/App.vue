<template>
  <div>
    <app-header></app-header>
    <list-games></list-games>
    <app-footer></app-footer>
    <games-modal></games-modal>
  </div>
</template>

<script>
import listGames from './components/listGames.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import gamesDetailsModal from './components/gameDetailsModal.vue'

export default {
  components:{
    'list-games': listGames,
    'app-header': Header,
    'app-footer': Footer,
    'games-modal': gamesDetailsModal,
  },
  data () {
    return {
    }
  },
  methods:{
  },
}
</script>

<style>
</style>
