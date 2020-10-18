<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <div class="card">
        <label class="block">
          <span class="form-label mb-2">Select a date</span>
          <date-picker v-model="date"></date-picker>
          <hr />
          <date-picker
            v-model="date2"
            format="DD/MM/YYYY"
            :options="{ showWeekNumber: true }"
          ></date-picker>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
import DatePicker from "./components/DatePicker"

export default {
  name: "App",

  components: {
    DatePicker
  },

  data() {
    return {
      date: "2020-10-18",
      date2: ""
    }
  }
}
</script>

<style src="./assets/css/app.css" />
