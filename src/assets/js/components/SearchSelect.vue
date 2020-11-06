<template>
  <div class="search-select" :class="{ 'is-active': isOpen }">
    <button class="search-select-input" type="button" @click="open">
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </button>

    <div class="search-select-dropdown" v-show="isOpen">
      <input v-model="search" class="search-select-search" />
      <ul v-show="filteredOptions.length > 0" class="search-select-options">
        <li
          v-for="option in filteredOptions"
          :key="option"
          class="search-select-option"
          @click="select(option)"
        >
          {{ option }}
        </li>
      </ul>

      <div v-show="filteredOptions.length === 0" class="search-select-empty">
        No results found for "{{ search }}"
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      value: "Destruction",
      search: "",
      options: [
        "Anthrax",
        "Dark Angel",
        "Death Angel",
        "Destruction",
        "Exodus",
        "Flotsam and Jetsam",
        "Kreator",
        "Megadeth",
        "Metallica",
        "Overkill",
        "Sepultura",
        "Slayer",
        "Testament"
      ]
    }
  },

  computed: {
    filteredOptions() {
      return this.options.filter(option => {
        return option.toLowerCase().startsWith(this.search.toLowerCase())
      })
    }
  },

  methods: {
    open() {
      this.isOpen = true
    },

    close() {
      this.isOpen = false
    },

    clearSearchInput() {
      this.search = ""
    },

    select(option) {
      this.value = option
      this.clearSearchInput()
      this.close()
    }
  }
}
</script>
