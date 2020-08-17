<template>
  <l-map ref="map" style="height: 100vh" :crs="crs" :minZoom="zoom">
    <l-image-overlay :url="mapImage" :bounds="boundss"></l-image-overlay>
    <l-marker
      v-for="marker in markers"
      :key="marker.name"
      :lat-lng="marker"
    ></l-marker>
    <l-marker :lat-lng="bounds2[0]"></l-marker>
    <l-marker :lat-lng="bounds2[1]"></l-marker>
  </l-map>
</template>

<script>
import L from 'leaflet'
import { LMap, LImageOverlay, LMarker } from 'vue2-leaflet'

export default {
  name: 'Map',
  components: {
    LMap,
    LImageOverlay,
    LMarker,
  },
  props: {
    markers: Array,
    boundss: Array,
  },
  data() {
    return {
      zoom: 5,
      mapImage: '/map5.jpg',
      bounds: [
        [-25.15, -25.3],
        [0.15, 10.2],
      ],
      bounds2: [
        [-26.33, -28.28],
        [7.32, 15.38],
      ],
      crs: L.CRS.Simple,
    }
  },
  mounted() {
    this.$refs.map.mapObject.setView([-12, -4], 1)
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
