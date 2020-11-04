<script>
export default {
  model: {
    prop: "tags",
    event: "update"
  },

  props: ["tags"],

  data() {
    return {
      input: ""
    }
  },

  computed: {
    newTag() {
      return this.input.trim()
    }
  },

  methods: {
    addTag() {
      if (this.newTag.length === 0 || this.tags.includes(this.newTag)) {
        return
      }
      this.$emit("update", [...this.tags, this.newTag])
      this.clearInput()
    },

    removeTag(tag) {
      this.$emit(
        "update",
        this.tags.filter(t => t !== tag)
      )
    },

    clearInput() {
      this.input = ""
    },

    // @input event listener for <input type="text" />
    onInput(e) {
      this.input = e.target.value
    }
  },

  // 3 slot-prop category
  render() {
    return this.$scopedSlots.default({
      // 1. data prop
      tags: this.tags,

      // 2. action prop
      removeTag: this.removeTag,

      addTag: this.addTag,

      inputValue: this.newTag,

      onInput: this.onInput
    })
  }
}
</script>
