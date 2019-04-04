<template>
    <tr>
        <td>{{ name }}</td>
        <td>{{ email }}</td>
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
        /* Make a pretty date for showing last_update */
        rented: function(){
            var options = { year: 'numeric', month: 'short', day: 'numeric', hour: 'numeric', minute: 'numeric' };
            var day  = new Date(this.transaction.rent_date);
            return day.toLocaleString("en-US", options);
        },
        /* Make a pretty date for showing last_update */
        returned: function(){
            if (this.transaction.return_date == null) return null;
            var options = {year: 'numeric', month: 'short', day: 'numeric', hour: 'numeric', minute: 'numeric' };
            var day  = new Date(this.transaction.return_date);
            return day.toLocaleString("en-US", options);
        }
    },
    props: ['id', 'name', 'email', 'transaction']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    td {
        text-align: left;
    }
</style>
