<script>
import contacts from "../../../../static/contacts.json"

export default {
  data() {
    return { contacts }
  },

  render(createElement) {
    return createElement(
      "ul",
      {},
      this.contacts.map(contact => {
        return createElement(
          "li",
          {},
          `${contact.name.first} ${contact.name.last}`
        )
      })
    )
  }
}
</script>

<style></style>
