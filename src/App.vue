<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto bg-white h-screen">
      <div class="flex justify-center pt-8">
        <hello-world>
          <h1 class="text-blue text-lg font-bold">Hello universe</h1>
        </hello-world>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./assets/js/components/HelloWorld"

export default {
  name: "App",

  components: { HelloWorld }
}
</script>

<style src="./assets/css/app.css" />
