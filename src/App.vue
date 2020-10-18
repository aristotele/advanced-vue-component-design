<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <div class="card">
        <label class="block">
          <span class="form-label mb-2">Select a date</span>
          <input
            :value="date"
            class="form-input"
            type="text"
            id="datepicker"
            placeholder="YYYY-MM-DD"
          />
        </label>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import Pikaday from "pikaday"

export default {
  data() {
    return {
      date: "2020-10-18"
    }
  },

  mounted() {
    const picker = new Pikaday({
      field: document.getElementById("datepicker"),
      format: "YYYY-MM-DD",
      onSelect: () => {
        this.date = picker.toString()
      }
    })
  }
}
</script>

<style src="./assets/css/app.css" />
