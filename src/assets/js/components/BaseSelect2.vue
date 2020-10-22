<template>
  <select class="w-full" ref="select2">
    <slot></slot>
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

    $(this.$el)
      .select2({ data: this.options })
      .val(this.value)
      .on("change", function() {
        // like @input
        vm.$emit("input", this.value)
      })
  },

  watch: {
    // need for non-UI (dom) change e.g. programmatic changes (or from vue dev-tools)
    value(value) {
      console.log("watch", value)

      $(this.$el)
        .val(value)
        .trigger("change")
    },

    // refresh data options (e.g on fresh data from ajax response)
    options(options) {
      // this is jquery
      $(this.$el)
        .empty()
        .select2({ data: options })
    }
  },

  destroyed() {
    // unbind any Select2 event explicitly bind ('change' in our case)
    // https://select2.org/programmatic-control/methods#event-unbinding
    $(this.$el)
      .off()
      .select2("destroy")
  }
}
</script>

<style></style>
