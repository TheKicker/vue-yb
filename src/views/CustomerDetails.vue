<template>
  <div class="container pt-4 pb-3">
    <h2 class="Htext2">Customer Details</h2>
    <div class="card" style="width: 80%; height: 20rem;">
      <div class="card-body" style="padding: 3rem;">
        <h4 class="card-title customerName">
          <strong>{{customer.name}} - {{ customer.id }}</strong>
        </h4>
        <h5 class="card-subtitle mb-2 text-muted">
          <i>{{this.role}}</i>
        </h5>
        <hr />
        <h6 class="card-text">
          <strong>Email:</strong>
          {{ customer.email }}
        </h6>
        <h6 class="card-text">
          <strong>Last Update:</strong>
          {{ this.updated }}
        </h6>
      </div>
    </div>
    <div id="spacer"></div>
  </div>
</template>
<script>
function customer({ id, name, email, isAdmin, updated_at }) {
  this.id = parseInt(id);
  this.name = name;
  this.email = email;
  this.isAdmin = isAdmin;
  this.updated_at = updated_at;
}
export default {
  data() {
    return {
      id: null,
      customer: Object,
    };
  },
  methods: {
    read() {
      let url = "https://codeflare.tech/api/customers/" + this.id;
      // let url = 'https://cavlemasters.com/api/users/' + this.id;
      window.axios.get(url).then(({ data }) => {
        this.customer = data;
      });
    },
  },
  computed: {
    /* using the isAdmin, return a text role */
    role: function () {
      return this.customer.isAdmin ? "Administrator" : "Customer";
    },
    /* MAke a pretty date for showing last_update */
    updated: function () {
      var options = {
        weekday: "long",
        year: "numeric",
        month: "long",
        day: "numeric",
        hour: "numeric",
        minute: "numeric",
      };
      var today = new Date(this.customer.updated_at);
      return today.toLocaleString("en-US", options);
    },
  },
  components: {},
  created() {
    this.id = this.$route.params.userId;
    this.read();
  },
};
</script>

<style>
.card {
  margin: auto;
}
.card-body {
  text-align: left;
}
</style>
