<template>
  <div>
    <div class="min-h-screen bg-grey-darker p-8">
      <div class="max-w-sm mx-auto">
        <user-settings-form :account-id="accountId"></user-settings-form>
      </div>
    </div>

    <modal-dialog :show="showCustomModal" @close="showCustomModal = false">
      <h1>Some text</h1>
      <button class="button bg-red p-2 rounded text-white">ehi</button>
    </modal-dialog>

    <announcement-modal
      :show="showAnnouncement"
      @close="showAnnouncement = false"
    ></announcement-modal>

    <!-- Need to be at the end of the docuemnt, outside, otherwise will inherite opacity -->
    <portal-target name="modals"></portal-target>
    <!--
    <portal-target name="dropdown"></portal-target>
    <portal-target name="tooltip"></portal-target>
     -->
  </div>
</template>

<script>
import UserSettingsForm from "./components/UserSettingsForm"
import AnnouncementModal from "./components/AnnouncementModal"
import ModalDialog from "./components/ModalDialog"

export default {
  components: { UserSettingsForm, AnnouncementModal, ModalDialog },

  data() {
    return {
      accountId: 7,
      showAnnouncement: false,
      showCustomModal: true
    }
  }
}
</script>

<style src="./assets/css/app.css" />
