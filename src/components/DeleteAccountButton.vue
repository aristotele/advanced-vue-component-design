<template>
  <button
    class="text-red hover:underline"
    type="button"
    @click="confirmDeleteModalOpen = true"
  >
    Delete Account

    <portal to="modals">
      <confirm-delete-modal
        :show="confirmDeleteModalOpen"
        @close="confirmDeleteModalOpen = false"
        :account-id="accountId"
      ></confirm-delete-modal>
    </portal>
  </button>
</template>

<script>
import ConfirmDeleteModal from "./ConfirmDeleteModal"

export default {
  props: ["accountId"],

  components: { ConfirmDeleteModal },

  data() {
    return {
      confirmDeleteModalOpen: false
    }
  }
}
</script>

<style></style>
