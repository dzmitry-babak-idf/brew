<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1 class="text-center text-info">Breweries List</h1>
            </div>
        </div>
        <div class="row">

            <div class="col-6">
                <BrewList
                        @mouse-over-brew="mouseOverBrew"
                        @mouse-left-brew="mouseLeftBrew"
                        :brews="brews"/>
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
                brews: [],
                normalIcon: [18, 18],
                largeIcon: [36, 36],
            }
        },
        mounted: function () {
            axios.get('https://api.openbrewerydb.org/breweries')
                .then((r) => {
                    this.brews = r.data.filter(r => r.state == 'Arizona')
                        .map(r => {
                            r.iconSize = this.normalIcon;
                            return r;
                        });
                })
            //https://api.openbrewerydb.org/breweries
        },
        methods: {
            mouseOverBrew: function (index) {
                this.brews[index].iconSize = this.largeIcon
            },
            mouseLeftBrew: function (index) {
                console.log(index + 'mouse left')
                this.brews[index].iconSize = this.normalIcon
            },
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

</style>
