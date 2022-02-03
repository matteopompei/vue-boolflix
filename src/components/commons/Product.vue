<template>
  <div class="product">
    <ul>
      <li>{{ product.title }}</li>
      <li>{{ product.original_title }}</li>
      <li>
        <img
          :src="
            require(`../../assets/img/flags/${product.original_language}.svg`)
          "
          alt=""
          class="lang"
        />
      </li>
      <li>{{ product.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    product: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/global.scss";

.product {
  padding: 5px 15px;
  width: 250px;
  height: fit-content;
  background: #000;

  ul {
    list-style: none;

    li {
      margin: 10px 0;

      .lang {
        width: 32px;
      }
    }
  }
}
</style>
