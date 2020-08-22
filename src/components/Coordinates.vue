<template>
  <div class="flex flex-col mt-32 mb-24">
    <div class="flex flex-row items-center ">
      <div class="inline-block relative w-16 m-1">
        <select
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          v-model.number="data.we"
          name="we"
          id="we"
        >
          <option value="-1">W</option>
          <option value="1">E</option>
        </select>
        <div
          class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
        >
          <svg
            class="fill-current h-4 w-4"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
          >
            <path
              d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
            />
          </svg>
        </div>
      </div>
      <input
        v-model.number="data.coord1"
        type="text"
        class="coord-input w-12"
        placeholder="0"
      />°
      <input
        v-model.number="data.coord2"
        type="text"
        class="coord-input w-12"
        placeholder="0"
      />'
      <input
        v-model.number="data.coord3"
        type="text"
        class="coord-input w-12"
        placeholder="0"
      />"
    </div>
    <div class="flex flex-row items-center">
      <div class="inline-block relative w-16 m-1">
        <select
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          v-model.number="data.sn"
          name="sn"
          id="sn"
        >
          <option value="-1">S</option>
          <option value="1">N</option>
        </select>
        <div
          class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
        >
          <svg
            class="fill-current h-4 w-4"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
          >
            <path
              d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
            />
          </svg>
        </div>
      </div>
      <input
        v-model.number="data.coord4"
        type="text"
        class="coord-input w-12"
        placeholder="0"
      />°
      <input
        v-model.number="data.coord5"
        type="text"
        class="coord-input w-12"
        placeholder="0"
      />'
      <input
        v-model.number="data.coord6"
        type="text"
        class="coord-input w-12"
        placeholder="0"
      />"
    </div>
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 m-8 rounded focus:outline-none focus:shadow-outline"
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
  margin: 0 auto;
  margin-top: 4em;
  padding-top: 30px;
  text-align: center;
}

.coord-input {
  @apply text-center shadow appearance-none border rounded py-2 px-3 m-1 text-gray-700 leading-tight;
}

.coord-input:focus {
  @apply outline-none shadow-outline;
}
</style>
