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
						-->
          <div class="font-bold">
            {{ functionProp(contact) }}
          </div>

          <!--
						with function props emulating scoped-slot.
						passing the local object as key-value { key: localObject }
						so the object to use up in the parent is wrapped by an object
						-->
          <div class="font-bold">
            {{ pseudoSlotScope({ ehi: contact }) }}
          </div>

          <!--
						with scoped-slot.
						passing the local object as key-value { key: localObject }
						so the object to use up in the parent is wrapped by an object
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
