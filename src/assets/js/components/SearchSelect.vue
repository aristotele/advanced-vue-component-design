<template>
  <div class="search-select" :class="{ 'is-active': isOpen }">
    <button class="search-select-input" type="button" @click="open">
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </button>

    <div class="search-select-dropdown" v-show="isOpen">
      <input class="search-select-search" />
      <ul class="search-select-options">
        <li
          v-for="option in options"
          :key="option"
          class="search-select-option"
          @click="select(option)"
        >
          {{ option }}
        </li>
      </ul>
    </div>
    <!-- <div class="search-select-empty">No results found</div> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      value: "Destruction",
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

  methods: {
    open() {
      this.isOpen = true
    },

    close() {
      this.isOpen = false
    },

    select(option) {
      this.value = option
      this.close()
    }
  }
}
</script>
