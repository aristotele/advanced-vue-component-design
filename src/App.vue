<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <div class="min-h-screen flex items-center justify-center">
        <button @click="modalOpen = true" type="button" class="btn btn-blue">
          Open Modal
        </button>
      </div>

      <announcement-modal
        :show="modalOpen"
        @close="modalOpen = false"
      ></announcement-modal>
    </div>
  </div>
</template>

<script>
import AnnouncementModal from "./assets/js/components/AnnouncementModal"

export default {
  name: "App",

  components: { AnnouncementModal },

  data() {
    return {
      modalOpen: false
    }
  }
}
</script>

<style src="./assets/css/app.css" />
