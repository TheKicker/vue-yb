<template>
    <tr>
        <td><img :src="this.imageUrl" class="imageThumbnail"> {{ title }}</td>
        <td>{{ rating }}</td>
        <td>{{ length}}</td>
        <td>{{ transaction.disc_type}}</td>
        <td>{{ this.rented }}</td>
        <td>{{ this.returned }}</td>
    </tr>
</template>

<script>
export default {
  data () {
    return {}
  },
  methods: {
  },
  computed: {
    /* Build URL for image */
    imageUrl: function () {
      return 'http://codeflare.tech/images/movie_' + this.transaction.movie_id + '.jpg'
    },
    /* Make a pretty date for showing last_update */
    rented: function () {
      var options = { year: 'numeric', month: 'short', day: 'numeric', hour: 'numeric', minute: 'numeric' }
      var day = new Date(this.transaction.rent_date)
      return day.toLocaleString('en-US', options)
    },
    /* Make a pretty date for showing last_update */
    returned: function () {
      if (this.transaction.return_date == null) return null
      var options = { year: 'numeric', month: 'short', day: 'numeric', hour: 'numeric', minute: 'numeric' }
      var day = new Date(this.transaction.return_date)
      return day.toLocaleString('en-US', options)
    }
  },
  props: ['id', 'title', 'rating', 'length', 'transaction']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    td {
        text-align: left;
    }
</style>
