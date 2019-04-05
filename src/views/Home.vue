<template>
  <div class="pt-4 pb-3">

    <h1>Yellow Box Customers</h1>

    <table class="table table-striped">
      <thead>
      <tr>
        <th>Title image</th>
        <th>Rating</th>
        <th>Length</th>
        <th>Disk Type</th>
        <th>Rented Date</th>
        <th>Return Date</th>
      </tr>
      </thead>
      <tbody>
      <!--listing component-->
      <movie-rental-component
              v-for="(movie, index) in movies"
              v-bind="movie"
              :index="index"
              :key="movie.id"
              @view="view"
              @rentals="rentals"
      ></movie-rental-component>
      </tbody>
    </table>
  </div>
</template>

<script>


    function Movie ({ id, title, rating, length, onDVD, onBluRay, updated_at}) {
        this.id = parseInt(id);
        this.title = title;
        this.rating = rating;
        this.length = length;
        this.onDVD = onDVD;
        this.onBluRay = onBluRay;
        this.updated_at = updated_at;
    }
    /* Go get the code for the customer-component tag that is in the template */
    import MovieRentalComponent from '@/components/CustomerRentalHistoryComponent.vue'
    export default {
        data () {
            return {
                movies: []
            }
        },
        methods: {
            read () {
                this.movies = [];
                // window.axios.get('https://cavlemasters.com/api/movies').then(({ data }) => {
                window.axios.get('https://codeflare.tech/api/movies').then(({ data }) => {
                    data.forEach(movie => {
                        this.movies.push(new Movie (movie))
                    })
                })
            },
            view (id) {
            },
            rentals (id) {
            }
        },
        components: {
            MovieRentalComponent
        },
        created () {
            this.read()
        }
    }
</script>
