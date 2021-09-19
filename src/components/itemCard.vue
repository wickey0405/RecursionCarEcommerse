<template>
    <div class="card m-2">
        <div class="card-body">
            <img v-bind:src="url" class="card-img-top" alt="...">
            <h5 class="card-title pt-2">{{ title }}</h5>
            <p class="card-text">Category: {{ category }}</p>
            <p class="card-text">Price: {{ price }}</p>
            <p class="card-text">Date: {{ date }}</p> 
        </div>
    </div>
</template>

<script>
export default {
  name: 'itemCard',
  props: {
    url: String,
    title: String,
    category: String,
    price: String,
    date: String
  },

}
</script>

<style scoped>
    .card{
        width: 18rem;
    }
</style>