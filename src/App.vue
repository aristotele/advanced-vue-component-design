<template>
  <div>
    <div class="min-h-screen bg-grey-darker p-8">
      <div class="max-w-sm mx-auto">
        <user-settings-form :account-id="accountId"></user-settings-form>
      </div>
    </div>

    <!-- without v-if this modal will overwrite the confirmDeleteModal declared above inside: user-setting-form > delete-account-button  -->
    <!-- this approach is usefull when only 1 instance of: modal, dropdown, tooltip should be shown at time -->
    <portal to="modals" v-if="showAnnouncement">
      <announcement-modal
        :show="showAnnouncement"
        @close="showAnnouncement = false"
      ></announcement-modal>
    </portal>

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

export default {
  components: { UserSettingsForm, AnnouncementModal },

  data() {
    return {
      accountId: 7,
      showAnnouncement: true
    }
  }
}
</script>

<style src="./assets/css/app.css" />
