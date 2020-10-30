<script>
export default {
  render(createElement) {
    return createElement(
      "h1",
      {
        attrs: {
          class: "text-lg text-blue font-bold"
        }
      },
      [this.$slots.default]
    )
  }
}
</script>

<style></style>
