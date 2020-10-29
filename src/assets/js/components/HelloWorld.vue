<script>
export default {
  props: ["tag"],

  render(createElement) {
    return createElement(
      this.tag,
      {
        attrs: {
          class: "btn btn-blue"
        },
        on: {
          click: () => alert("clicked")
        }
      },
      "Hello World"
    )
  }
}
</script>

<style></style>
