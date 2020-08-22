<template>
  <div class="flex flex-col items-center">
    <button
      class="block bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 m-2 rounded focus:outline-none focus:shadow-outline"
      v-on:click="clearMarkers"
    >
      Clear Markers
    </button>
    <button
      class="block bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 my-6 rounded focus:outline-none focus:shadow-outline"
      v-on:click="share"
    >
      Share
    </button>
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
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
