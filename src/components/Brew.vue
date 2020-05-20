<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1 class="text-center text-info">Breweries List</h1>
            </div>
        </div>
        <div class="row">

            <div class="col-6">
                <BrewList :brews="brews"/>
            </div>
            <div class="col-6">
                <BrewMap :brews="brews"/>
            </div>
        </div>
        <!-- /.row -->
    </div>
    <!-- /.container -->
</template>

<script>
    import axios from 'axios'
    import BrewList from "./BrewList";
    import BrewMap from "./BrewMap";
    //https://api.openbrewerydb.org/breweries
    export default {
        name: 'Brew',
        components: {BrewMap, BrewList},
        data: function () {
            return {
                brews: []
            }
        },
        mounted: function () {
            axios.get('https://api.openbrewerydb.org/breweries')
                .then((r) => {
                    this.brews = r.data
                    console.log(r.data)
                })
            //https://api.openbrewerydb.org/breweries
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

</style>
