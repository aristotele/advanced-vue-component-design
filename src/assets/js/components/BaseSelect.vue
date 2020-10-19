<template>
  <select
    :value="value"
    @input="$emit('input', $event.target.value)"
    class="form-input"
  >
    <option
      v-for="option in options"
      :key="option.id"
      :value="option.id"
      v-text="option.value"
    ></option>
  </select>
</template>

<script>
export default {
  props: ["value", "options"]
}
</script>

<style></style>
