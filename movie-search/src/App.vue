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
  margin: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;  
}

body {
  background: linear-gradient(to right, rgb(0, 0, 0), rgb(67, 67, 67));
  color: #fff;
}

</style>
