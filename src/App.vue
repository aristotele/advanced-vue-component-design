<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <!--
        The Goal is: use data and variables defined in the child <contact-list> to make something here, in the parent <App>

        Using props: define function to be exectuted in child component;
        works but cannot manipulate html
        <contact-list :pseudo-slot="({ ehi }) => ehi.name.first">

        Using scoped Slot: it's the same as using (function) props AND allow html manipulation
      -->
      <contact-list
        :function-prop="ehi => ehi.name.first"
        :pseudo-slot-scope="
          ObjWrappingSlotProp => ObjWrappingSlotProp.ehi.name.first
        "
      >
        <a
          slot-scope="ObjWrappingSlotProp"
          :href="`/contacts/${ObjWrappingSlotProp.mySlotProp.id}`"
        >
          {{ ObjWrappingSlotProp.mySlotProp.name.first }}
        </a>
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
