<template>
  <span
    class="toggle"
    role="checkbox"
    tabindex="0"
    @click="toggle"
    @keydown.space.prevent="toggle"
    :aria-checked="isChecked.toString()"
  ></span>
</template>

<script>
export default {
  name: "ToggleComponent",

  model: {
    prop: "is-checked",
    event: "checked"
  },

  props: ["is-checked"],

  methods: {
    toggle() {
      this.$emit("checked", !this.isChecked)
    }
  }
}
</script>

<style></style>
