<template>
  <div class="search-select" :class="{ 'is-active': isOpen }">
    <button
      class="search-select-input"
      type="button"
      @click="open"
      ref="button"
    >
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </button>

    <div class="search-select-dropdown" v-show="isOpen">
      <input v-model="search" ref="search" class="search-select-search" />
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
  props: ["value", "options", "filterFunction"],

  data() {
    return {
      isOpen: false,
      search: ""
    }
  },

  mounted() {
    console.log(this.filterFunction)
  },

  computed: {
    filteredOptions() {
      // We've passed the function declaration (the logic we would like to execute for filtering)
      // as a prop, so we just need to invoke it, passing as parameter the local's component data
      // here we 'decide' the api, meaning the order of parameters; the parent must adhere to this order
      return this.filterFunction(this.search, this.options)
    }
  },

  methods: {
    open() {
      this.isOpen = true
      this.$nextTick(() => {
        this.$refs.search.focus()
      })
    },

    close() {
      this.isOpen = false
      this.$refs.button.focus()
    },

    clearSearchInput() {
      this.search = ""
    },

    select(option) {
      this.$emit("input", option)
      this.clearSearchInput()
      this.close()
    }
  }
}
</script>
