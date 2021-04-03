<template>
  <l-map ref="map" style="height: 100vh" v-on:click="dropMarker" :crs="crs" :minZoom="zoom">
    <l-image-overlay :url="mapImage" :bounds="boundss"></l-image-overlay>
    <l-marker
      v-for="marker in markers"
      :key="marker.name"
      :lat-lng="marker"
    ></l-marker>
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
      mapImage: '/map2.jpg',
      bounds: [
        [-25.15, -25.3],
        [0.15, 10.2],
      ],
      crs: L.CRS.Simple,
    }
  },
  mounted() {
    this.$refs.map.mapObject.setView([-12, -4], 1)
  },
  methods: {
    dropMarker(e) {
      this.$emit('dropMarker', e.latlng)
    },
  },
  watch: {
    markers: function (val) {
      const marker = val[val.length - 1];
      this.$refs.map.mapObject.setView([marker.lat, marker.lng], 6)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
