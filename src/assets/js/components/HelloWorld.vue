<script>
import contacts from "../../../../static/contacts.json"

export default {
  data() {
    return { contacts }
  },

  render(createElement) {
    // parent wrapper <div> with array of children [<h1>, <ul>]
    return createElement("div", {}, [
      createElement("h1", {}, "My ugly header"),
      createElement(
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
    ])
  }
}
</script>

<style></style>
