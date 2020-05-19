<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1 class="text-center text-info">Breweries List</h1>
<!--                <h2 class="text-center">{{msg}} {{name}}</h2>-->
            </div>
            <!-- /.col-12 -->
        </div>
        <div class="row">

            <div class="col-6 brew-list">
                <div class="card" style="width: 18rem;">
                    <ul class="list-group list-group-flush">
                        <li class="list-group-item" v-for="brew in brews">{{brew.name}}, {{brew.state}}</li>

                    </ul>
                </div>
            </div>
            <div class="col-6"><h2 class="text-center">right</h2></div>
        </div>
        <!-- /.row -->
    </div>
    <!-- /.container -->
</template>

<script>
    import axios from 'axios'
    //https://api.openbrewerydb.org/breweries
    export default {
        name: 'Brew',
        data: function(){
            return{
                brews:[]
            }
        },
        mounted: function() {
            axios.get('https://api.openbrewerydb.org/breweries')
            .then((r)=>{
                this.brews = r.data
                console.log(r.data)
            })
            //https://api.openbrewerydb.org/breweries
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
    .brew-list{
        overflow-y: scroll;
        height: 96vh;
        li{
            &:hover{
                background-color: darkgrey;
            }
        }
    }
</style>
