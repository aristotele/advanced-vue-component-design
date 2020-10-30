<script>
export default {
  render() {
    // is a VNode, so we can return it, directly in the render function
    console.log(
      this.$scopedSlots.default({
        myProperty: "Bitch",
        anotherProp: "You are a"
      })
    )

    return this.$scopedSlots.default({
      myProperty: "Bitch",
      anotherProp: "You are a"
    })
  }
}
</script>

<style></style>
