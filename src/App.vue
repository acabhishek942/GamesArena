<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ greeting() }}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'Games-Arena'
    }
  },
  methods:{
    greeting: function(){
      return 'Welcome to Game Arena';
    }
  }
}
</script>

<style>
</style>
