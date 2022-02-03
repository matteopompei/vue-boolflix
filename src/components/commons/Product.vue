<template>
  <div class="product">
    <img
      :src="'https://image.tmdb.org/t/p/w342' + product.poster_path"
      :alt="product.original_title"
      class="poster"
      v-if="product.poster_path != null"
    />
    <img
      src="../../assets/img/poster-notfound.png"
      alt=""
      class="poster"
      v-else
    />
    <div class="info">
      <ul>
        <li><strong>Titolo:</strong> {{ product.title }}</li>
        <li><strong>Titolo originale:</strong> {{ product.original_title }}</li>
        <li>
          <img
            :src="
              require(`../../assets/img/flags/${product.original_language}.svg`)
            "
            :alt="product.original_language"
            class="lang"
          />
        </li>
        <li><strong>Voto:</strong> {{ product.vote_average }}</li>
      </ul>
    </div>
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
  position: relative;
  width: 250px;
  height: 350px;
  background: #000;

  .poster {
    width: 250px;
    height: 350px;
    object-fit: cover;
  }

  .info {
    position: absolute;
    top: 0;
    width: 250px;
    height: 350px;
    opacity: 0;
    padding: 5px 15px;
    background: #000;
    transition: opacity 0.3s;

    &:hover {
      opacity: 1;
    }

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
}
</style>
