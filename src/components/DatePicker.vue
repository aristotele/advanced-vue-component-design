<template>
  <input
    :value="value"
    class="form-input"
    type="text"
    ref="datepicker"
    placeholder="YYYY-MM-DD"
  />
</template>

<script>
/* eslint-disable no-unused-vars */
import Pikaday from "pikaday"

export default {
  props: {
    value: { required: true },
    format: { default: "YYYY-MM-DD" },
    options: { default: {} }
  },

  mounted() {
    const picker = new Pikaday({
      field: this.$refs.datepicker,
      format: this.format,
      onSelect: () => {
        this.$emit("input", picker.toString())
      },
      ...this.options
    })
  }
}
</script>

<style></style>
