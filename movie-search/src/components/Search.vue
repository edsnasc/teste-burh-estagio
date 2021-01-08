<template>
<div>
  <div class="search">
    <input type="text" v-model="searchKey" placeholder="Pesquisar Filme">
    <button @click="getMovie">Pesquisar</button>
  </div>
    <br>
    <p>{{movie}}</p>
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
        justify-content: center;

    }

    
</style>