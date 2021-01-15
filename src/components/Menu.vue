<template>
  <div>
    <img :src="posterImage" :alt="item.name" />
    <div class="itemname">
      <a @click="toggleExpansion(key)" >{{ item.name }}</a>
       <ul v-show="isExpanded(key)">
      <li>{{item.details}}</li>
    </ul>
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
    itemPath: function () {
      return `/meals/${this.item.id}`;
    }
  },
  data() {
return {
//isExpanded: false,
expandedGroup: []
}
},
methods:{
isExpanded(key) {
return this.expandedGroup.indexOf(key) !== -1;
},
toggleExpansion(key) {
if (this.isExpanded(key))
this.expandedGroup.splice(this.expandedGroup.indexOf(key), 1);
else
this.expandedGroup.push(key);
}
}
}
</script>

<style scoped>
.itemname {
  font-size: 1.3rem;
  font-weight: bold;
}
.image{
    width:100%;
}
</style>
