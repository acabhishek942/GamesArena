<template>
  <div>
    <app-header v-bind:title="title"></app-header>
    <list-games></list-games>
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
      title: 'Games Arena'
    }
  },
  methods:{
  }
}
</script>

<style>
</style>
