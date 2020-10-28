<template>
  <div class="card">
    <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
    <div>
      <div
        v-for="contact in contacts"
        :key="contact.id"
        class="flex items-center spaced-y-6"
      >
        <img
          :src="contact.picture.medium"
          class="h-12 w-12 rounded-full block mr-2"
          alt=""
        />
        <div>
          <!--
						with function props.
						passing directly the local object
						Invoke functionProp using local variable `contact` as actual parameter
						for the function defined in <App> who has `ehi` as formal parameter
						-->
          <div class="font-bold">
            {{ functionProp(contact) }}
          </div>

          <!--
						with function props emulating scoped-slot.
						Invoke pseudoSlotScope passing the local object as key-value { dummykey: localObject }
						This simulate they way scoped-slot works { mySlotProp: contact } (look below)
						-->
          <div class="font-bold">
            {{ pseudoSlotScope({ dummyKey: contact }) }}
          </div>

          <!--
						with scoped-slot.
						passing the local object as key-value { mySlotProp: contact }

						This way I can access <contact-list> contact variable inside parent component <App>
						-->
          <div class="font-bold">
            <slot :my-slot-prop="contact"></slot>
          </div>

          <div class="text-grey-dark">
            {{ contact.email }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ContactList",

  props: ["functionProp", "pseudoSlotScope"],

  data() {
    return {
      contacts: []
    }
  },

  created() {
    fetch("/contacts.json")
      .then(response => response.json())
      .then(contacts => (this.contacts = contacts))
  }
}
</script>

<style></style>
