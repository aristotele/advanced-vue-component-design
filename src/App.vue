<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <div class="flex justify-center pt-8">
        <fetch-json url="/contacts.json">
          <template slot-scope="{ json: contacts, loading }">
            <div class="card">
              <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
              <div v-if="loading">
                Loading ...
              </div>
              <contact-list v-else :contacts="contacts"></contact-list>
            </div>
          </template>
        </fetch-json>
      </div>
    </div>
  </div>
</template>

<script>
import FetchJson from "./assets/js/components/FetchJson"
import ContactList from "./assets/js/components/ContactList"

export default {
  name: "App",

  components: { FetchJson, ContactList }
}
</script>

<style src="./assets/css/app.css" />
