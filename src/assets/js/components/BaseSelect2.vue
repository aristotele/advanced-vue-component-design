<template>
  <select class="form-input" id="select2">
    <option
      v-for="option in options"
      :key="option.id"
      :value="option.id"
      v-text="option.value"
    ></option>
  </select>
</template>

<script>
/* eslint-disable no-unused-vars */
import $ from "jquery"
import select2 from "select2"
import "select2/dist/css/select2.min.css"

export default {
  props: ["value", "options"],

  mounted() {
    var vm = this

    $("#select2")
      .select2()
      .on("change", function() {
        // like @input
        vm.$emit("input", this.value)
      })
  },

  watch: {
    value(value) {
      console.log("watch", value)

      $("#select2")
        .val(value)
        .trigger("change")
    },

    options(options) {
      // this is jquery
      $(this.$el)
        .empty()
        .select2({ data: options })
    }
  }
}
</script>

<style></style>
