<template>
    <div class="row map">
        <l-map :zoom="zoom" :center="center">
            <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
            <l-marker :lat-lng="marker"></l-marker>
        </l-map>
    </div>

</template>

<script>
    import {LMap, LTileLayer, LMarker} from 'vue2-leaflet';


    export default {
        name: "BrewMap",
        data: function () {
            return {
                zoom: 16,
                center: L.latLng(53.852056, 27.611501),
                url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
                attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
                marker: L.latLng(53.852056, 27.611501),
            }
        },
        components: {
            LMap,
            LTileLayer,
            LMarker,
        },
    }
</script>

<style scoped>
    .map {
        height: 93vh;
        margin: 0;
    }
</style>