<template>
  <form class="card" @submit.prevent="submit">
    <h1 class="text-2xl font-bold mb-6">Your Settings</h1>
    <label class="block mb-6">
      <span class="form-label mb-2">Email Address</span>
      <input v-model="email" class="form-input" placeholder="you@example.com" />
    </label>
    <div class="mb-8">
      <span class="form-label mb-2">Newsletter</span>
      <div class="flex justify-between items-center">
        <p class="mr-4">Send you occasional news and updates.</p>
        <toggle-component v-model="receiveNewsletter"></toggle-component>
      </div>
    </div>
    <div class="flex justify-between" style="opacity: 0.5;">
      <button
        class="text-red hover:underline"
        type="button"
        @click="confirmDeleteModalOpen = true"
      >
        Delete Account
      </button>
      <confirm-delete-modal
        :show="confirmDeleteModalOpen"
        @close="confirmDeleteModalOpen = false"
        :account-id="accountId"
      ></confirm-delete-modal>
      <button type="button" class="btn btn-blue">Update Settings</button>
    </div>
  </form>
</template>

<script>
import ToggleComponent from "./ToggleComponent"
import ConfirmDeleteModal from "./ConfirmDeleteModal"

export default {
  name: "UserSettingsForm",

  props: ["accountId"],

  components: {
    ToggleComponent,
    ConfirmDeleteModal
  },

  data() {
    return {
      email: "",
      receiveNewsletter: false,
      confirmDeleteModalOpen: false
    }
  },

  methods: {
    submit() {
      console.log("Submitting preferences...", {
        email: this.email,
        receiveNewsletter: this.receiveNewsletter
      })
    }
  }
}
</script>

<style></style>
