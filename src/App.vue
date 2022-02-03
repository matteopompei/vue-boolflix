<template>
  <div id="app">
    <header>
      <a href="#" class="logo">Boolflix</a>
      <Search @research="getResearch" />
    </header>
    <main>
      <Product
        v-for="(element, index) in moviesArr"
        :key="index"
        :product="element"
      />
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
      moviesArr: [],
      searchQuery: "",
    };
  },
  methods: {
    getCatalog() {
      axios
        .get(this.apiURLmovies, {
          params: {
            api_key: "2074120094dfaee1cbc64c89325caff2",
            query: this.searchQuery,
          },
        })
        .then((response) => {
          console.log(response);
          this.moviesArr = response.data.results;
          console.log(this.moviesArr);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    getResearch(inputSearch) {
      this.searchQuery = inputSearch;
      this.getCatalog();
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
  background: #191919;
  min-height: calc(100vh - 87px);
}
</style>
