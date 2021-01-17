<template>
  <div>
    <div v-if="!isOpen(key)">
      <img class="productImage" :src="posterImage" :alt="item.name" />
      <div class="itemname">
        <a @click="toggleModal(key)" class="name shadow-lg">{{ item.name }}</a>
      </div>
    </div>
    <div v-else class="overlay ">
      <div
        class="detailContainer"
        v-show="isOpen(key)"
        :style="{
          backgroundImage: 'url(' + detailImage + ')',
          backgroundSize: 'cover',
        }"
      >
        <div class="details">{{ item.details }}</div>
        <div class="priceContainer">
          <div class="price">£ {{ item.prices.price.price }}</div>
        </div>
        <button class="closebutton" @click="toggleModal(key)">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["item"],
  computed: {
    posterImage: function () {
      return `${this.item.image}`;
    },
    detailImage: function () {
      return `${this.item.image2}`;
    },

    itemPath: function () {
      return `/meals/${this.item.id}`;
    }
  },
  data() {
    return {
      key: 0,
      //isOpen: false,
      modalGroup: [],
      name: ''
    }
  },
  methods: {
    isOpen(key) {
      return this.modalGroup.indexOf(key) !== -1;
    },
    toggleModal(key) {
      if (this.isOpen(key))
        this.modalGroup.splice(this.modalGroup.indexOf(key), 1);
      else
        this.modalGroup.push(key);
    },

  }
}
</script>

<style scoped>
.itemname {
  font-size: 1.3rem;
  font-weight: bold;
}
.image {
  width: 100%;
}
.detailContainer {
  display:grid;
  min-height: 10rem;
}
.priceContainer {
  background: url("../assets/images/tag.png") no-repeat left;
  background-size: 40%;
  min-height: 5rem;
  text-align: left;
  font-size: 1rem;
  text-indent: 3.2rem;
}
.price {
  padding-top: 1.8rem;
  color:black;
  font-size:0.8rem;
}
.details {
  background-color: rgba(255, 255, 255, 0.5);
  padding: 1rem;
  list-style-type: none;
  font-family: "Xanh Mono", sans-serif;

  font-weight: 800;
  color: black;
}
.name {
  color: #a1dac9;
  cursor: pointer;
}
.name:hover {
  color: black;
  cursor: pointer;
}
.productImage {
  max-width: 100%;
}
.closebutton{
  color:white;
  background:#288267;
}
.overlay{
  background: rgb(161 218 201);
}
</style>
