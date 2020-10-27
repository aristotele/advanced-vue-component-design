<template>
  <div class="modal-backdrop" v-show="show">
    <div class="modal">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: ["show"],

  methods: {
    cancel() {
      this.$emit("close")
    }
  },

  watch: {
    show: {
      immediate: true,
      handler: show => {
        if (show) {
          document.body.style.setProperty("overflow", "hidden")
        } else {
          document.body.style.removeProperty("overflow")
        }
      }
    }
  },

  created() {
    const listener = document.addEventListener("keydown", e => {
      if (this.show && e.keyCode === 27) {
        this.cancel()
      }
    })

    this.$once("hook:beforeDestroy", () => {
      console.log("removing listener")
      document.removeEventListener("keydown", listener)
    })
  }
}
</script>

<style></style>
