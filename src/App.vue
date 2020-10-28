<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <contact-list :pseudo-slot="contact => contact.name.first">
        <!-- {{ contact.name.first }} -->
      </contact-list>
    </div>
  </div>
</template>

<script>
import ContactList from "./assets/js/components/ContactList"

export default {
  name: "App",

  components: { ContactList }
}
</script>

<style src="./assets/css/app.css" />
