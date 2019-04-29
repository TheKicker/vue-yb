<template>
    <div>
    <div class="cardMovie">
    <img :src="this.imageUrl" class="card-img-top" style="border-radius: 25px;">
    <div class="card-body">
        <h3 class="card-title" align="center"><strong> {{ title }} </strong></h3>
        <h5 class="card-text" align="center"> <i>{{ rating }}</i><strong>&nbsp;&nbsp;|&nbsp;</strong><i>{{ length }} min</i></h5>
    </div>
    <div class="card-links">
        <button id="button1" class="btn btn-md btn-success"><router-link :to="'/movie-details/' + this.id" style="color: white">Details</router-link></button>
        <button id="button2" class="btn btn-md btn-dark"><router-link :to="'/movie-details/' + this.id + '/rented'" style="color: white">Rentals</router-link></button>
    </div>
    </div>
    </div>
</template>

<script>
export default {
  data () {
    return {}
  },
  methods: {
    view () {
      // this.$emit('view', this.id);
      console.log('Component Viewing id:' + this.id)
      // this.$router.push({ name: 'customer-details', params: { id: 3 } })
      let myRoute = '/movie-details/3'
      this.$router.push(myRoute)
    },
    rentals () {
      this.$emit('rentals', this.id)
    }
  },
  computed: {
    /* Build URL for image */
    imageUrl: function () {
      return 'http://codeflare.tech/images/movie_' + this.id + '.jpg'
      // return   "https://cavlemasters.com/api/movie_" + this.id + ".jpg";
    }
  },
  props: ['id', 'title', 'rating', 'length', 'onDVD', 'onBluRay']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
