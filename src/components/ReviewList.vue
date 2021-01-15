<template>
  <div>
    <div class="review-container">
      <h2>Orders</h2>
      <ul>
        <li v-for="(review, index) in reviews" :key="index">
          <b>{{ review.name }}</b> of company <b>{{ review.company }}</b> gave sent this <b>enquiry</b>:
          <br />
          <div class="reviewContent" >

          "{{ review.review }}"
          </div>
          <br />
          ...and gave <b>{{ review.rating }} stars</b>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    reviews: {
      type: Array,
      required: true
    }
  },

}
</script>

<style scoped>
.reviewContent{
  border:1px solid rgb(161 218 201);
  padding: 1rem;
}
</style>