<script>
export default {
  data() {
    return {
      contacts: []
    }
  },

  created() {
    fetch("/contacts.json")
      .then(response => response.json())
      .then(contacts => (this.contacts = contacts))
  },

  render() {
    return this.$scopedSlots.default({
      contacts: this.contacts
    })
  }
}
</script>

<style></style>
