<template>
  <div>
    <div style="opacity: 0.5;" class="min-h-screen bg-grey-darker p-8">
      <user-settings-form
        @open:confirm-delete-modal="confirmDeleteModalOpen = true"
      ></user-settings-form>
    </div>

    <!-- Need to be at the end of the docuemnt, outside, otherwise will inherite opacity -->
    <confirm-delete-modal
      :show="confirmDeleteModalOpen"
      @close="confirmDeleteModalOpen = false"
      :account-id="accountId"
    ></confirm-delete-modal>
  </div>
</template>

<script>
import UserSettingsForm from "./components/UserSettingsForm"
import ConfirmDeleteModal from "./components/ConfirmDeleteModal"

export default {
  components: { UserSettingsForm, ConfirmDeleteModal },

  data() {
    return {
      confirmDeleteModalOpen: false,
      accountId: 7
    }
  }
}
</script>

<style src="./assets/css/app.css" />
