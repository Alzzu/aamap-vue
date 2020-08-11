<template>
  <div>
    <button v-on:click="clearMarkers">Clear Markers</button>
    <button v-on:click="share">Share</button>
  </div>
</template>

<script>
export default {
  name: 'Controls',
  data() {
    return {}
  },
  methods: {
    clearMarkers() {
      this.$emit('clearMarkers')
    },
    share() {
      this.$emit('share')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  display: block;
  font-size: 24px;
  margin: 2em;
}
</style>
