<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <!-- <base-select v-model="selectedColor" :options="colors"></base-select> -->

      <hr />

      <base-select2 v-model.number="selectedColor" :options="colors">
        <option disabled value="0">Select one</option>
      </base-select2>

      <hr />

      <base-select2 v-model.number="selectedColor" :options="colors">
        <option disabled value="0">Select one</option>
      </base-select2>
    </div>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */

import BaseSelect2 from "./assets/js/components/BaseSelect2"

export default {
  name: "App",

  components: { BaseSelect2 },

  data() {
    return {
      selectedColor: 1,
      colors: [
        // ! need specific data format https://select2.org/data-sources/formats
        { id: 1, text: "red" },
        { id: 2, text: "green" },
        { id: 3, text: "orange" }
      ]
    }
  }
}
</script>

<style src="./assets/css/app.css" />
