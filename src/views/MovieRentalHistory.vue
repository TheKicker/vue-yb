<template>
    <div class="about pt-4 pb-3">
        <h1>Movie Rentals</h1>

        <table class="table table-striped">
            <thead>
            <tr>
                <th>Name</th>
                <th>Email</th>
                <th>Type</th>
                <th>Rented</th>
                <th>Returned</th>
            </tr>
            </thead>
            <tbody>
            <movie-rental-history-component
                    v-for="(customer, index) in customers"
                    v-bind="customer"
                    :index="index"
                    :key="customer.id"
            ></movie-rental-history-component>

            </tbody>
        </table>
    </div>
</template>
<script>
import MovieRentalHistoryComponent from '@/components/MovieRentalHistoryComponent.vue'
function Customer ({ id, name, email, pivot }) {
  this.id = parseInt(pivot.id)
  this.name = name
  this.email = email
  this.transaction = pivot
}
export default {
  data () {
    return {
      id: null,
      title: '',
      customers: []
    }
  },
  methods: {
    read () {
      // let url = 'https://cavlemasters.com/api/movies/' + this.id + '/rentals';
      let url = 'https://codeflare.tech/api/movies/' + this.id + '/rentals'
      window.axios.get(url).then(({ data }) => {
        this.title = data[0].title
        console.log(this.title)
        console.log(data[0])
        data[0].rentals.forEach(customer => {
          this.customers.push(new Customer(customer))
        })
      })
    }
  },
  components: {
    MovieRentalHistoryComponent
  },
  created () {
    this.id = this.$route.params.userId
    this.read()
  }
}
</script>

<style scoped lang="scss">
    th {
        text-align: left;
    }
</style>
