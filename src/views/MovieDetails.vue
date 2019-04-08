<template>
    <div class="pt-4 pb-3" >
        <!--<h3> {{ movie.title }}</h3>-->
        <div class="cardMovie" style="width: 40%;" align="center">
            <img class="card-body">
            <h5 class="card-title">{{movie.title }} </h5>
                <img :src="this.imageUrl" class="thumbnailDetails" align="center">
                <div class="detailsTextBox">
                    <p class="card-text"> Movie ID #{{movie.id}}</p>
                    <p class="card-text">Description: {{ movie.description }}</p>
                    <p class="card-text">Rating: {{ movie.rating }}</p>
                    <p class="card-text">Length: {{ movie.length }}</p>
                    <p class="card-text">Available on DVD: {{ movie.onDVD }}</p>
                    <p class="card-text">Available on BluRay: {{ movie.onBluRay }}</p>
                </div>
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
