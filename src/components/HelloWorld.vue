<template>
<div id="app">
    <app-button></app-button>
    </div>
</template>

<script>
export default {
  name: 'App',
 
  components: {
    'app-button':{
      template: '<p>App Button Component Mounted!</p>',
      mounted() {
        alert("sak khan");
      }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app li {
  list-style-type: none;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

</style>
