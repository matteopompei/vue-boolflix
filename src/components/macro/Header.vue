<template>
  <header>
    <a href="#" class="logo">Boolflix</a>
    <Search />
  </header>
</template>

<script>
import Search from "../commons/Search.vue";
export default {
  name: "Header",
  components: { Search },
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/global.scss";

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
</style>
