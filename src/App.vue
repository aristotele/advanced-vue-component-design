<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <base-select v-model="selectedColor" :options="colors"></base-select>

      <hr />
    </div>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import $ from "jquery"
import select2 from "select2"
import "select2/dist/css/select2.min.css"

import BaseSelect from "./assets/js/components/BaseSelect"

export default {
  name: "App",

  components: { BaseSelect },

  data() {
    return {
      selectedColor: "",
      colors: [
        { id: 1, value: "red" },
        { id: 2, value: "green" },
        { id: 3, value: "orange" }
      ]
    }
  },

  methods: {
    triggerSelectInput(event) {
      // console.log("event", event)
      // this.selectedColor = event
    }
  },

  mounted() {
    var vm = this

    // $("#select2")
    //   .select2()
    //   .on("change", function() {
    //     // console.log(this.value)
    //     vm.selectedColor = this.value
    //     // vm.$emit("input", this.value)
    //   })
  }
}
</script>

<style src="./assets/css/app.css" />
