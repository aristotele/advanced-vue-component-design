<script>
export default {
  model: {
    prop: "tags"
  },

  props: ["tags"],

  // 3 slot-prop category
  render() {
    return this.$scopedSlots.default({
      // 1. data prop
      tags: this.tags
    })
  }
}
</script>
