<script>
export default {
  model: {
    prop: "tags",
    event: "update"
  },

  props: {
    tags: { required: true },
    removeOnBackspace: { default: true }
  },

  data() {
    return {
      inputValue: ""
    }
  },

  computed: {
    newTag() {
      return this.inputValue.trim()
    }
  },

  methods: {
    removeTag(tag) {
      this.$emit(
        "update",
        this.tags.filter(t => t !== tag)
      )
    },

    addTag() {
      if (this.newTag.length === 0 || this.tags.includes(this.newTag)) {
        return
      }
      this.$emit("update", [...this.tags, this.newTag])
      this.clearInput()
    },

    clearInput() {
      this.inputValue = ""
    },

    handleBackspace() {
      if (this.newTag.length === 0) {
        this.$emit("update", this.tags.slice(0, -1))
      }
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

      // 3. binding props
      inputProps: {
        value: this.inputValue
      },

      inputEvents: {
        input: e => {
          this.inputValue = e.target.value
        },

        keydown: e => {
          if (e.key === "Backspace" && this.removeOnBackspace) {
            this.handleBackspace()
          }

          if (e.keyCode === 13) {
            e.preventDefault()
            this.addTag()
          }
        }
      },

      // now removeButtonEvent is a function that return an object
      // this way we can accept argument from the consumer
      removeButtonEvent: tag => {
        return {
          click: () => {
            console.log(tag)
            this.removeTag(tag)
          }
        }
      }
    })
  }
}
</script>
