<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <!-- <base-select v-model="selectedColor" :options="colors"></base-select> -->

      <hr />

      <base-select2
        v-model.number="selectedColor"
        :options="colors"
      ></base-select2>
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
        { id: 1, value: "red" },
        { id: 2, value: "green" },
        { id: 3, value: "orange" }
      ]
    }
  }
}
</script>

<style src="./assets/css/app.css" />
