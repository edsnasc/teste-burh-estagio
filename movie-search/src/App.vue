<template>
  <div id="app">
    <Search />
  </div>
</template>

<script>
import Search from './components/Search'

export default {
  name: 'App',
  components: { Search }
}
</script>

<style>
* {
  
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;  
}

body {
  margin: 10px;
  background: linear-gradient(to right, rgb(0, 0, 0), rgb(67, 67, 67));
  color: #fff;
}

</style>
