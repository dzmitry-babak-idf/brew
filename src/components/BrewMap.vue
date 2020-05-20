<template>
    <div class="row map">
        <!--        {{brews}}-->
<!--        <p>Center is {{currentCenter}}, zoom is {{currentZoom}}</p>-->
        <l-map
                @update:zoom="zoomUpdate"
                @update:center="centerUpdate"
                :zoom="zoom"
                :center="center">
            <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
            <l-marker
                    :key="index"
                    v-for="(brew, index) in brews"
                    :lat-lng="latLng(brew.latitude, brew.longitude)"
            >
                <l-icon
                        :icon-size="iconSize"
                        :icon-url="icon"
                ></l-icon>
            </l-marker>
        </l-map>
    </div>

</template>

<script>
    import {LMap, LTileLayer, LMarker, LIcon} from 'vue2-leaflet';
    import beer from '../assets/beer.png'

    export default {
        name: "BrewMap",
        props: {
            brews: Array
        },
        data: function () {
            return {
                zoom: 7,
                currentZoom: 7,
                // center: L.latLng(53.852056, 27.611501),
                center: L.latLng(33.856659, -112.423096),
                currentCenter: L.latLng(34.0, -112.5),
                url: 'https://tile.thunderforest.com/outdoors/{z}/{x}/{y}.png?apikey=ea703157e00f4d46819468d22e1418d9',
                attribution: 'contributors',
                marker: L.latLng(53.852056, 27.611501),
                icon: beer,
                iconSize: [18, 18],
            }
        },
        components: {
            LMap,
            LTileLayer,
            LMarker,
            LIcon,
        },
        methods: {
            latLng: function (lat, lng) {
                return L.latLng(lat, lng)
            },
            centerUpdate: function (center) {
                this.currentCenter = center
            },
            zoomUpdate: function (zoom) {
                this.currentZoom = zoom

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