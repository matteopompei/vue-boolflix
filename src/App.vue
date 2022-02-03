<template>
  <div id="app">
    <header>
      <a href="#" class="logo">Boolflix</a>
      <Search @research="getResearch" />
    </header>
    <main>
      <div class="title">Movies</div>
      <div class="container">
        <Product
          v-for="(element, index) in moviesArr"
          :key="index"
          :product="element"
        />
      </div>

      <div class="title">Series</div>
      <div class="container">
        <Product
          v-for="(element, index) in seriesArr"
          :key="index"
          :product="element"
        />
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Search from "./components/commons/Search.vue";
import Product from "./components/commons/Product.vue";

export default {
  components: { Search, Product },
  name: "App",

  data() {
    return {
      apiURLmovies: "https://api.themoviedb.org/3/search/movie",
      apiURLseries: "https://api.themoviedb.org/3/search/tv",
      moviesArr: [],
      seriesArr: [],
      searchQuery: "",
    };
  },
  methods: {
    getMovies() {
      axios
        .get(this.apiURLmovies, {
          params: {
            api_key: "2074120094dfaee1cbc64c89325caff2",
            query: this.searchQuery,
          },
        })
        .then((response) => {
          this.moviesArr = response.data.results;
          console.log(this.moviesArr);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    getSeries() {
      axios
        .get(this.apiURLseries, {
          params: {
            api_key: "2074120094dfaee1cbc64c89325caff2",
            query: this.searchQuery,
          },
        })
        .then((response) => {
          this.seriesArr = response.data.results;
          console.log(this.seriesArr);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    getResearch(inputSearch) {
      this.searchQuery = inputSearch;
      this.getMovies();
      this.getSeries();
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/global.scss";

header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 25px 15px;
  background: #000;

  & > .logo {
    color: rgb(255, 0, 0);
    font-size: 2rem;
    font-weight: 400;
    text-transform: uppercase;
    text-decoration: none;
    letter-spacing: 2px;
  }
}

main {
  padding: 50px 100px;
  min-height: calc(100vh - 87px);
  background: #191919;

  .title {
    margin: 0 100px 50px 50px;
    font-size: 3rem;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin: auto auto 100px auto;
    width: 85%;
  }
}
</style>
