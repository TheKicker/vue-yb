<template>
    <div class="container pt-3 pb-2" >
        <!--<h3> {{ movie.title }}</h3>-->
            <div class="cardMovieDetails">
                <h3 class="movieDetailsTitle">{{movie.title }} </h3>
                <div class="innerDetailsBox row">
                        <div class="movieDetailsImage">
                            <img :src="this.imageUrl">
                        </div>
                        <div class="movieDetailsTextBox">
                            <p class="card-text"><strong>Movie ID #</strong>000{{movie.id}}</p>
                            <p class="card-text"><strong>Length: </strong>{{movie.length}} &nbsp; | &nbsp; <strong>Rating:</strong> {{movie.rating}}</p>
                            <p class="card-text"><strong>Description: </strong>{{ movie.description }}</p>
                            <p class="card-text"><strong> DVD: </strong>{{movie.onDVD}} &nbsp; | &nbsp; <strong>BluRay:</strong> {{movie.onBluRay}}</p>
                        </div>
                </div>
                <div style="height: 5rem;"></div>
            </div>
        <div id="spacer"></div>
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
