<template>
  <div>
    <div class="container">
        <div class="hero">Food And Drink</div>
      <ul>
            <li v-for="(item,index) in data.items" :key="index">
              <Menu v-bind:item="item" />
            </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Menu from "./Menu.vue";
export default {

  name: "ItemsList",
  data() {
    return {
      data: [],
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
  },
  components: {
    Menu,
  },
}
</script>

<style  scoped>
.hero{
  font-size:10rem;
    font-family:'Xanh Mono', sans-serif;
    color:rgb(161 218 201);
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
  background: rgb(161 218 201);
  list-style-type: none;
  grid-row-gap: 1rem;
}
</style>