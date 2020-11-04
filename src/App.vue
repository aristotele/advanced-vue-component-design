<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Renderless</label>

      <renderless-tag-input v-model="tags">
        <template slot-scope="{ tags, removeTag, inputProps, inputEvents }">
          <div class="tag-input">
            <span v-for="tag in tags" :key="tag" class="tag-input-tag">
              <span>{{ tag }}</span>
              <button
                type="button"
                class="tag-input-remove"
                @click="removeTag(tag)"
              >
                &times;
              </button>
            </span>
            <!--
              How it works?
              https://vuejs.org/v2/guide/components-props.html#Passing-the-Properties-of-an-Object
              It's the same as writing
              :value="inputProps.value"
              but with only v-bind="obj" -> all object key will be translated to v-bind:objKey="obj.objKey"
              -->
            <input
              v-bind="inputProps"
              v-on="inputEvents"
              class="tag-input-text"
              placeholder="Add tag..."
            />
          </div>
        </template>
      </renderless-tag-input>
    </div>

    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Original</label>
      <tag-input v-model="tags"></tag-input>
    </div>
  </div>
</template>

<script>
import TagInput from "./assets/js/components/TagInput"
import RenderlessTagInput from "./assets/js/components/RenderlessTagInput"

export default {
  name: "App",

  components: { TagInput, RenderlessTagInput },

  data() {
    return {
      tags: ["awesome", "magnific", "super"]
    }
  }
}
</script>

<style src="./assets/css/app.css" />
