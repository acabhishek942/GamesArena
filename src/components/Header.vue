<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: {
  title: {
    type: String,
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
header{
  background: lightgreen;
  padding: 10px;
  position: fixed;
  top: 0;
  width: 100%;
  text-align: center;
}
h1{
  color: #222;
  text-align: center;
}
</style>
