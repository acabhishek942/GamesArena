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
  background: #222;
  padding: 10px;
  position: fixed;
  top: 0;
  width: 100%;
  text-align: center;
}
h1{
  color: lightgreen;
  text-align: center;
}
</style>
