<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Renderless Stacked Layout</label>

      <renderless-tag-input v-model="tags" :remove-on-backspace="false">
        <div
          class="stacked-tag-input"
          slot-scope="{
            tags,
            removeButtonEvent,
            inputProps,
            inputEvents,
            addTag
          }"
        >
          <div class="stacked-tag-input-form">
            <input
              class="form-input"
              placeholder="Add tag..."
              v-bind="inputProps"
              v-on="inputEvents"
            />
            <button class="btn btn-indigo" @click="addTag">Add Tag</button>
          </div>
          <ul class="stacked-tag-list">
            <li v-for="tag in tags" :key="tag">
              {{ tag }}
              <button
                type="button"
                class="stacked-tag-link"
                v-on="removeButtonEvent(tag)"
              >
                Remove
              </button>
            </li>
          </ul>
        </div>
      </renderless-tag-input>
    </div>

    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Renderless</label>

      <renderless-tag-input v-model="tags">
        <template
          slot-scope="{ tags, removeButtonEvent, inputProps, inputEvents }"
        >
          <div class="tag-input">
            <span v-for="tag in tags" :key="tag" class="tag-input-tag">
              <span>{{ tag }}</span>

              <!--
                in this case the 'binding-prop' need some context that only the parent knows about
                so we make removeButtonEvent in the renderless component a function which accept an argument and return an object
                -->
              <button
                type="button"
                class="tag-input-remove"
                v-on="removeButtonEvent(tag)"
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
