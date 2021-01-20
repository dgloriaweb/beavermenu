<template>
  <div>
    <div class="container">
      <form class="review-form" @submit.prevent="onSubmit">
        <h3>Order Form</h3>
        <label for="name">Name:</label>
        <br/>
        <input type="text" id="name" v-model="name" />
        <br/>
        <label for="name">Company:</label>
        <br/>
        <input type="text" id="name" v-model="company" />
        <br/>
        <label for="review">Enquiry:</label>
        <br/>
        <textarea
          name=""
          id="review"
          cols="30"
          rows="10"
          v-model="review"
        ></textarea>
        <br/>
        <label for="rating">Rating:</label>
        <select name="" id="rating" v-model.number="rating">
          <option value="5">5</option>
          <option value="4">4</option>
          <option value="3">3</option>
          <option value="2">2</option>
          <option value="1">1</option>
        </select>
        <br/>
        <input type="submit" class="button" value="Submit" />
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'Evan You',
      company: 'Vue',
      review: 'I would like to get price offer for 1000 cheesecakes by 2nd Feb 2021. Thanks',
      rating: 5
    }
  },
  methods: {
    onSubmit() {
      if (this.name === '' || this.company === '' || this.review === '' || this.rating === null) {
        alert('Review is incomplete. Please fill out every field.')
        return
      }
      let productReview = {
        name: this.name,
        company: this.company,
        review: this.review,
        rating: this.rating,
      }
      this.$emit('review-submitted', productReview)

      this.name = ''
      this.company = ''
      this.review = ''
      this.rating = null
    }
  }
}
</script>

<style  scoped>

input, textarea {
  border: .1rem dotted grey;
}
h3{
  font-weight: 800;
}
</style>