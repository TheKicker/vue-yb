<template>
    <div class="card" style="width: 18rem">
    <img :src="this.imageUrl" class="card-img-top">
    <div class="card-body">
        <h3 class="card-title"> {{ title }} </h3>
        <h4 class="card-text"> {{ rating }} </h4>
        <h4 class="card-text"> Length: {{ length }} </h4>
    </div>
    <div class="card-links">
        <button class="btn btn-sm btn-success"><router-link :to="'/movie-details/' + this.id">Details</router-link></button>
        <button class="btn btn-sm btn-dark"><router-link :to="'/movie-details/' + this.id + '/rented'">Rentals</router-link></button>
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
        let myRoute = '/movie-details/3';
        this.$router.push(myRoute);
      },
      rentals () {
        this.$emit('rentals', this.id);
      }
    },
    computed:{
        /* Build URL for image */
        imageUrl: function(){
            return   "https://cloudflare.tech/api/movies_" + this.id + ".jpg";
            // return   "https://cavlemasters.com/api/movies_" + this.id + ".jpg";
        },
    },
    props: ['id', 'title', 'rating', 'length', 'onDVD', 'onBluRay']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
