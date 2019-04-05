<template>
    <div class="container">
        <h1>Yellow Bucket Customers</h1>

        <table class="table">
            <thead>
            <tr>
                <th>Name</th>
                <th>Email</th>
                <th>Role</th>
                <th>Actions</th>
            </tr>
            </thead>
            <tbody>
            <customer-component
                    v-for="(customer, index) in customers"
                    v-bind="customer"
                    :index="index"
                    :key="customer.id"
                    @view="view"
                    @rentals="rentals"
            ></customer-component>
            </tbody>
        </table>
        <div id="spacer"></div>
    </div>
</template>
<script>
/* Go get the code for the customer-component tag that is in the template */
import CustomerComponent from '@/components/CustomerComponent.vue'
function Customer ({ id, name, email, isAdmin, updated_at }) {
  this.id = parseInt(id)
  this.name = name
  this.email = email
  this.isAdmin = isAdmin
  this.updated_at = updated_at
}
export default {
  data () {
    return {
      customers: []
    }
  },
  methods: {
    read () {
      this.customers = []
      // window.axios.get('https://cavlemasters/api/customers').then(({ data }) => {
      window.axios.get('https://codeflare.tech/api/customers').then(({ data }) => {
        data.forEach(customer => {
          this.customers.push(new Customer(customer))
        })
      })
    },
    view (id) {
    },
    rentals (id) {
    }
  },
  components: {
    CustomerComponent
  },
  created () {
    this.read()
  }
}
</script>

<style>

</style>
