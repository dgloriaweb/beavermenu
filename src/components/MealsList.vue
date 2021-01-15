<template>
  <div>
    <div class="container">
      <div class="hero">Food And Drink</div>
      <ul>
        <li v-for="(item, index) in data.items" :key="index">
          <Menu v-bind:item="item" />
        </li>
      </ul>
      <div class="reviewContainer">
        <div class="reviews">
          <review-list v-if="reviews.length" :reviews="reviews" />
        </div>
        <div class="form">
          <review-form @review-submitted="addReview" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Menu from "./Menu.vue";
import ReviewForm from "./ReviewForm.vue";
import ReviewList from "./ReviewList.vue";
export default {

  name: "ItemsList",
  data() {
    return {
      data: [],
      reviews: []
    };
  },
  created: function () {
    this.fetchData();
  },
  methods: {
    fetchData: async function () {
      try {
        const res = await fetch(
          "https://dev.menu.ninja/api/menu/156?key=8j5vfe%24*pfb**rzt&pretty=1"
        );

        const apiresource = await res.json();
        this.data = apiresource.menu;
      } catch (e) {
        console.log(e);
      }
    },
    addReview(review) {
      this.reviews.push(review)
    }
  },
  components: {
    Menu,
    ReviewForm,
    ReviewList
  },
}
</script>

<style  scoped>
.hero {
  font-size: 10rem;
  font-family: "Xanh Mono", sans-serif;
  color: rgb(161 218 201);
}

.container {
  margin: auto;
}
ul {
  display: grid;
  list-style-type: none;
  padding: 1rem;
  margin: 0;
  grid-row-gap: 2rem;
  grid-column-gap: 1rem;
  grid-template-columns: repeat(3, 1fr);
}
li {
  font-family: "Hachi Maru Pop";
  list-style-type: none;
  grid-row-gap: 1rem;
}
.reviewContainer{
  max-width:20rem;
  margin:auto
}
</style>