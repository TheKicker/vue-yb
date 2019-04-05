<template>
    <div class="pt-4 pb-3">
        <h3>Movie Details</h3>
        <div class="card" style="width: 50%;">
            <img class="card-body">
                <img :src="this.imageUrl" class="thumbnail">
                <h5 class="card-title">{{movie.title}} - {{ movie.id }}</h5>
                <p class="card-text">Description: {{ movie.description }}</p>
                <p class="card-text">Rating: {{ movie.rating }}</p>
                <p class="card-text">Length: {{ movie.length }}</p>
                <p class="card-text">Available on DVD: {{ movie.onDVD }}</p>
                <p class="card-text">Available on BluRay: {{ movie.onBluRay }}</p>
            </div>
        </div>

</template>
<script>
function Movie ({ id, title, description, rating, length, onDVD, onBluRay }) {
  this.id = parseInt(id)
  this.title = title
  this.description = description
  this.rating = rating
  this.length = length
  this.onDVD = onDVD
  this.onBluRay = onBluRay
}
export default {
  data () {
    return {
      id: null,
      movie: Object
    }
  },
  methods: {
    read () {
      let url = 'https://codeflare.tech/api/movies/' + this.id
      // let url = 'https://cavlemasters.com/api/movies/' + this.id;
      window.axios.get(url).then(({ data }) => {
        this.movie = data
      })
    }
  },
  computed: {
    /* Build URL for image */
    imageUrl: function () {
      // return "https://cavlemasters.com/api/movies_" + this.movie.id + ".jpg";
      return 'http://codeflare.tech/images/movie_' + this.movie.id + '.jpg'
    }
  },
  components: {
  },
  created () {
    this.id = this.$route.params.userId
    this.read()
  }
}
</script>

<style>
    .card {
        margin: auto;
    }
    .card-body {
        text-align: left;
    }
</style>
