<template>
  <div id="app" class="flex">
    <div class="flex flex-col items-center lg:mx-32 md:mx-16 mx-8">
      <Coordinates @addMarker="addMarker" />
      <Controls @clearMarkers="clearMarkers" @share="share" />
    </div>
    <Map :markers="markers" :boundss="bounds" />
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
      bound1: -25,
      bound2: -25.04,
      bound3: 0,
      bound4: 10.05,
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
  computed: {
    bounds: function() {
      return [
        [this.bound1, this.bound2],
        [this.bound3, this.bound4],
      ]
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap');

#app {
  font-family: 'Open Sans', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
