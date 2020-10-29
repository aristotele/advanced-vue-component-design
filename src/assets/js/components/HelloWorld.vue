<script>
import ToggleInput from "./ToggleInput"

export default {
  data() {
    return {
      isToggled: true
    }
  },

  render(createElement) {
    // By declaring the prop 'value' and 'input' event we're simulating v-model in the render function
    return createElement(ToggleInput, {
      props: {
        value: this.isToggled
      },
      on: {
        input: newValue => (this.isToggled = newValue)
      }
    })
  }
}
</script>

<style></style>
