<script>
import PrimaryButton from "./PrimaryButton"

export default {
  components: {
    PrimaryButton
  },

  render(createElement) {
    return createElement(
      PrimaryButton,
      {
        nativeOn: {
          click: () => alert("clicked!")
          // click() {
          //   alert("clicked")
          // }
        }
      },
      "Hello World"
    )
  }
}
</script>

<style></style>
