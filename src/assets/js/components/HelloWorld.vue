<template>
  <ul>
    <li v-for="contact in contacts" :key="contact.id">
      {{ contact.name.first }} {{ contact.name.last }}
    </li>
  </ul>
</template>

<script>
import contacts from "../../../../static/contacts.json"

export default {
  data() {
    return { contacts }
  }
}
</script>

<style></style>
