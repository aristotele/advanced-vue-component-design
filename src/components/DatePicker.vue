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
  props: ["value"],

  mounted() {
    const picker = new Pikaday({
      field: this.$refs.datepicker,
      format: "YYYY-MM-DD",
      onSelect: () => {
        this.$emit("input", picker.toString())
      }
    })
  }
}
</script>

<style></style>
