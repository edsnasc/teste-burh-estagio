<template>
  <div class="search" >
      <form action="#">
          <input type="text" v-model="searchmovie" placeholder="Pesquisar Filme"><button type="submit">Pesquisar</button>
      </form>    
  </div>
</template>

<script>
import axios from 'axios'
import { baseApiUrl, ApiKey } from '@/global'

export default {
    name: 'Search',
    data: function(){
        return {
            searchmovie: "Batman"

        }
    },
    methods: {
        getMovie() {
            const id = this.searchmovie
            const url = `${baseApiUrl}${id}${ApiKey}`
            axios.get(url).then(res => {
                console.log(res)
            })
        }
    },
    mounted() {
        this.getMovie()
    }   
}
</script>

<style>
    .search {
        display: flex; 
        justify-content: center;
        align-items: center;
    }

    
</style>