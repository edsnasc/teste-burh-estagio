<template>
<div class="search">
  <img class="logo" src="@/assets/logo.png" alt="logo" width="250" height="200">
  <h1>Search Movies</h1>
  <div >
      <input type="text" v-model="searchKey" placeholder="Pesquisar Filme">
      <button @click="getMovie">Pesquisar</button>
  </div>
</div>
</template>

<script>
import axios from 'axios'
import { baseApiUrl, ApiKey } from '@/global'

export default {
    name: 'Search',
    data: function() {
        return {
            searchKey:'',
            movie:[]

        }
    },
    methods: {
        getMovie() {
            const id = this.searchKey
            const url = `${baseApiUrl}${id}${ApiKey}`
            axios.get(url).then(res => {
                this.movie = res
            })

        }
    }
}
</script>

<style>
   
    .search {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;  
    }

    .search input {
        width: 700px;
        height: 20px;
        outline: none; 
    }

    .search button {
        height: 25px;
    }
    
</style>