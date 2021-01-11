<template>
  <div>
    <header class="header-container">
      <img class="logo" src="@/assets/logo.png" alt="logo" width="250" height="200"/>
      <h1>Search Movies & Series</h1>
    </header>
    <div class="search-container">
      <input type="text" v-model="searchKey" placeholder="Search movie..." />
      <button @click="getMovie">Search</button>
    </div>
    <div class="information-container" v-if="movie.Response == 'True'">
      <div class="information">
        <img :src="movie.Poster" alt="poster" />
        <ul>
          <li><strong>Title: </strong> {{ movie.Title }}</li>
          <li><strong>Year: </strong> {{ movie.Year }}</li>
          <li><strong>Runtime: </strong> {{ movie.Runtime }}</li>
          <li><strong>Genre: </strong> {{ movie.Genre }}</li>
          <li><strong>Director: </strong> {{ movie.Director }}</li>
          <li><strong>Writer: </strong> {{ movie.Writer }}</li>
          <li><strong>Actors: </strong> {{ movie.Actors }}</li>
          <li><strong>Country: </strong> {{ movie.Country }}</li>
          <li><strong>Production: </strong> {{ movie.Production }}</li>
          <li><strong>Plot: </strong> {{ movie.Plot }}</li>
        </ul>
      </div>
    </div>
    <div class="error" v-else>
      <strong>{{ movie.Error }}</strong>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { baseApiUrl, ApiKey } from "@/global";

export default {
  name: "Search",
  data: function () {
    return {
      searchKey: "",
      movie:[],
    };
  },
  methods: {
    getMovie() {
      const id = this.searchKey;
      const url = `${baseApiUrl}${id}${ApiKey}`;
      axios.get(url).then((res) => {
        this.movie= res.data;
      });
    }
  }
};
</script>

<style>
.header-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.search-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.search-container input {
  width: 700px;
  height: 25px;
  font-size: 15px;
  outline: none;
}

.search-container button {
  height: 25px;
  font-size: 18px;
  border: none;
  color: #fff;
  background-color: red;
  box-shadow: 0 0 20px black;
  outline: none;
}

.search-container button:hover {
  background-color: #e57373;
}

.information-container {
  display: flex;
  justify-content: center;
}

.information {
  width: 1000px;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 20px black;
  background: linear-gradient(to right,rgb(15, 32, 39),rgb(32, 58, 67),rgb(44, 83, 100));
}

.information ul {
  list-style: none;
  padding-left: 10px;
}
.information img {
  position: relative;
  width: 260px;
  height: 350px;
  padding: 10px 0px 10px 10px;
}

.error {
  text-align: center;
}

@media screen and (max-width: 900px) {
  .information {
  width: 100%;
  height: 100%;  
  flex-direction: column;
  }

  .logo {
    width: 200px;
    height: 150px;
  }
}
</style>