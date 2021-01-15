<template>
  <div>
    <img :src="posterImage" :alt="item.name" />
    <div class="itemname">
      <a @click="toggleExpansion(key)" >{{ item.name }}</a>
      <div
        class="detailContainer"
        v-show="isExpanded(key)"
        :style="{
          backgroundImage: 'url(' + detailImage + ')',
          backgroundSize: 'cover',
        }"
      >
        <div class="details">{{ item.details }}</div>
        <div class="priceContainer">
          <div class="price">

           £ {{ item.prices.price.price }}</div>
          </div>
        <!-- <div class="details" :style="{backgroundImage:'url('+priceImage+')',backgroundSize: 'cover'}">{{ item.prices.price.price }}</div> -->
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
      key:0,
      //isExpanded: false,
      expandedGroup: [],
      name:''
    }
  },
  methods: {
    isExpanded(key) {
      return this.expandedGroup.indexOf(key) !== -1;
    },
    toggleExpansion(key) {
      if (this.isExpanded(key))
        this.expandedGroup.splice(this.expandedGroup.indexOf(key), 1);
      else
        this.expandedGroup.push(key);
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
.detailContainer{
   background-color:#a1dac9;
 min-height:10rem;
}
.priceContainer {
  background:   url('../assets/images/tag.png') no-repeat left;
  background-size: 40%;
   min-height:5rem;
   text-align:left;
   font-size:1rem;
   text-indent:4rem;
}
.price{
  padding-top: 1.5rem;
}
.details {
  background-color:rgba(255,255,255,0.5);
  padding: 1rem;
  list-style-type: none;
  font-family: Monotype;
  font-weight: 300;
  color:black;
}
</style>
