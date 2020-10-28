<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <!-- here I'm defining the function to be exectuted in child -->
      <contact-list
        :pseudo-slot="ObjWrappingSlotProp => ObjWrappingSlotProp.ehi.name.first"
      >
        <!-- {{ contact.name.first }} -->
        <template slot-scope="ObjWrappingSlotProp">
          {{ ObjWrappingSlotProp.mySlotProp.name.first }}
        </template>
      </contact-list>
    </div>
  </div>
</template>

<script>
import ContactList from "./assets/js/components/ContactList"

export default {
  name: "App",

  components: { ContactList },

  methods: {
    log(obj) {
      console.log("ehi", obj)
      // console.log("ehi", this)
    }
  }
}
</script>

<style src="./assets/css/app.css" />
