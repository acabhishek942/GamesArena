<template>
    <footer>
        <p>Copyright 2018 {{ title }}</p>
    </footer>
</template>
<script>
export default {
    data(){
        return{
          title: 'Games Arena',
        }
    }
}
</script>
<style scoped>
footer{
  background: #222;
  padding: 6px;
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  text-align: center;
}
p{
  color: lightgreen;
  text-align: center;
}
</style>
