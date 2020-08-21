<template>
  <div class="coord-form">
    <div class="flex flex-row items-center ">
      <select
        class="shadow border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        v-model.number="data.we"
        name="we"
        id="we"
      >
        <option value="-1">W</option>
        <option value="1">E</option>
      </select>
      <input
        v-model.number="data.coord1"
        type="text"
        class="text-center shadow appearance-none border rounded w-12 py-2 px-3 m-1 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        placeholder="0"
      />°
      <input
        v-model.number="data.coord2"
        type="text"
        class="text-center shadow appearance-none border rounded w-12 py-2 px-3 m-1 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        placeholder="0"
      />'
      <input
        v-model.number="data.coord3"
        type="text"
        class="text-center shadow appearance-none border rounded w-12 py-2 px-3 m-1 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        placeholder="0"
      />"
    </div>
    <div class="flex flex-row items-center">
      <select
        class="shadow border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        v-model.number="data.sn"
        name="sn"
        id="sn"
      >
        <option value="-1">S</option>
        <option value="1">N</option>
      </select>
      <input
        v-model.number="data.coord4"
        type="text"
        class="text-center shadow appearance-none border rounded w-12 py-2 px-3 m-1 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        placeholder="0"
      />°
      <input
        v-model.number="data.coord5"
        type="text"
        class="text-center shadow appearance-none border rounded w-12 py-2 px-3 m-1 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        placeholder="0"
      />'
      <input
        v-model.number="data.coord6"
        type="text"
        class="text-center shadow appearance-none border rounded w-12 py-2 px-3 m-1 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        placeholder="0"
      />"
    </div>
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
      v-on:click="addMarker"
    >
      Add marker
    </button>
  </div>
</template>

<script>
export default {
  name: 'Coordinates',
  data() {
    return {
      data: {
        we: -1,
        sn: -1,
        coord1: 0,
        coord2: 0,
        coord3: 0,
        coord4: 0,
        coord5: 0,
        coord6: 0,
      },
    }
  },
  methods: {
    addMarker() {
      this.$emit('addMarker', this.data)
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.coord-form {
  font-size: 24px;
  margin: 0 auto;
  margin-top: 4em;
  padding-top: 30px;
  text-align: center;
}
select {
  font-size: 24px;
  padding: 3px;
  margin: 3px;
  width: 2.5em;

  border: 2px solid #bfbfbf;
  border-radius: 4px;
}

button {
  padding: 10px;
  font-weight: 500;
  font-size: 24px;
  margin: 2em;
}
</style>
