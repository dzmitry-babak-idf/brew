<template>
    <div class="row map">
<!--        {{brews}}-->
        <l-map :zoom="zoom" :center="center">
            <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
            <l-marker
                    :key="index"
                    v-for="(brew, index) in brews"
                    :lat-lng="latLng(brew.latitude, brew.longitude)"
            ></l-marker>
        </l-map>
    </div>

</template>

<script>
    import {LMap, LTileLayer, LMarker} from 'vue2-leaflet';


    export default {
        name: "BrewMap",
        props: {
            brews: Array
        },
        data: function () {
            return {
                zoom: 3,
                // center: L.latLng(53.852056, 27.611501),
                center: L.latLng(58.383551,-116.01905),
                url: 'https://tile.thunderforest.com/outdoors/{z}/{x}/{y}.png?apikey=ea703157e00f4d46819468d22e1418d9',
                attribution: 'contributors',
                marker: L.latLng(53.852056, 27.611501),
            }
        },
        components: {
            LMap,
            LTileLayer,
            LMarker,
        },
        methods: {
            latLng: function (lat, lng) {
                return L.latLng(lat, lng)
            }
        },
    }
</script>

<style scoped>
    .map {
        height: 93vh;
        margin: 0;
    }
</style>