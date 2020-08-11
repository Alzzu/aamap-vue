<template>
  <div id="app" class="container">
    <div>
      <Coordinates @addMarker="addMarker" />
      <Controls @clearMarkers="clearMarkers" @share="share" />
    </div>

    <Map :markers="markers" />
  </div>
</template>

<script>
import Map from './components/Map.vue'
import Coordinates from './components/Coordinates.vue'
import Controls from './components/Controls.vue'

export default {
  name: 'App',
  components: {
    Map,
    Coordinates,
    Controls,
  },
  data() {
    return {
      markers: [
        { name: '', lat: -0.311388888, lng: -7.59 },
        {
          name: '',
          lat: -15.63444444,
          lng: -2.06861111,
        },
        { name: '', lat: -24.04388889, lng: 0.818888889 },
      ],
      shareUrl: '',
    }
  },
  beforeMount() {
    const queryString = window.location.search
    const urlParams = new URLSearchParams(queryString)
    if (urlParams.has('markers')) {
      const markers = atob(urlParams.get('markers'))
      this.markers = JSON.parse(markers)
    }
  },
  methods: {
    addMarker(data) {
      let lng = (data.coord1 + data.coord2 / 60 + data.coord3 / 3600) * data.we
      let lat = (data.coord4 + data.coord5 / 60 + data.coord6 / 3600) * data.sn

      this.markers.push({ name: '', lat, lng })
    },
    clearMarkers() {
      this.markers = []
    },
    share() {
      const currentUrl = window.location.href
      const url =
        currentUrl.split('?')[0] +
        '?markers=' +
        btoa(JSON.stringify(this.markers))
      this.shareUrl = url
      this.doCopy(url)
    },
    doCopy(url) {
      this.$copyText(url).then(
        function(e) {
          alert('URL copied to your clipboard')
          console.log(e)
        },
        function(e) {
          alert('Failed to copy the url')
          console.log(e)
        }
      )
    },
  },
}
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container {
  display: grid;
  grid-template-columns: 1fr 3fr;
}
</style>
