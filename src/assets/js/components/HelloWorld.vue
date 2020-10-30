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
      [
        this.$scopedSlots.default({
          myProperty: "Bitch",
          anotherProp: "You are a"
        })
      ]
    )
  }
}
</script>

<style></style>
