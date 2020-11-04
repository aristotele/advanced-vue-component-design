<script>
export default {
  model: {
    prop: "tags"
  },

  props: ["tags"],

  methods: {
    removeTag(tag) {
      this.$emit(
        "input",
        this.tags.filter(t => t !== tag)
      )
    }
  },

  // 3 slot-prop category
  render() {
    return this.$scopedSlots.default({
      // 1. data prop
      tags: this.tags,

      // 2. action prop
      removeTag: this.removeTag
    })
  }
}
</script>
