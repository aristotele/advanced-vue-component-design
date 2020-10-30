<script>
export default {
  props: ["url"],
  data() {
    return {
      json: []
    }
  },

  created() {
    fetch(this.url)
      .then(response => response.json())
      .then(json => (this.json = json))
  },

  render() {
    return this.$scopedSlots.default({
      json: this.json
    })
  }
}
</script>

<style></style>
