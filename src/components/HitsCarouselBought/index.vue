<template>
  <ais-hits>
    <ul class="hits-list hits-list-modal" slot-scope="{ items }">
      <li
        class="hit-list"
        v-for="item in items"
        :key="item.objectID"
        @click="selectedProduct(item)"
      >
        <div class="image-wrapper">
          <img
            :src="'https://www.lgcstandards.com/' + item.brand.logo.url"
            alt=""
          />
        </div>
        <div class="infos">
          <ais-highlight class="title" :hit="item" attribute="name" />
        </div>
        <p class="prices">
          To view pricing
          <br>
          <span>Login/Register</span>
        </p>
      </li>
    </ul>
  </ais-hits>
</template>

<script>
import { mapActions } from "vuex";
export default {
  methods: {
    ...mapActions("SearchModule", ["selectedProduct"]),
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/variables/variables.scss";
.hits-list-modal {
  flex-wrap: nowrap;
  display: -webkit-box;
  overflow-x: scroll;
  padding: 1rem 0rem;
  list-style-type: none;
  li {
    width: 250px !important;
    .image-wrapper {
      width: 100%;
      img {
        width: 100%;
        background-image: #f2f2f2;
        object-fit: cover;
        object-position: center;
        position: relative;
      }
    }
    .infos {
      .title {
        font-size: 0.9rem;
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
        font-family: $main-font;
        color: #000;
      }
    }
    p {
      font-size: 1rem;
      font-weight: 300;
    }
  }
}

.hits-list {
  justify-content: center;
  align-items: center;
  width: 100%;
  .hit-list {
    width: 30%;
    display: -webkit-flex;
    display: flex;
    -webkit-flex-direction: column;
    flex-direction: column;
    border: #f2f2f2 solid 1px;
    margin: 0.2rem;
    padding: 1rem;
    cursor: pointer;
  }
}

ul {
  list-style: none;
  font-family: $main-font;
  color: #000;
}
.prices {
  span {
    color: $second-color;
    font-weight: 500;
  }
}
</style>
