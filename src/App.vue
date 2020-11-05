<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto card mt-8">
      <accordion-list>
        <accordion-item :item-id="1">
          <template slot="header">Item A</template>
          <template slot="content">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec
            finibus auctor massa, vitae posuere sem tincidunt eget. Duis non
            vestibulum diam. Pellentesque eleifend interdum mollis. Donec
            porttitor dui enim. Maecenas a semper sem. Nunc molestie turpis
            vitae sem auctor, non venenatis velit ultricies.
          </template>
        </accordion-item>

        <accordion-item :item-id="2">
          <template slot="header">Item B</template>
          <template slot="content">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec
            finibus auctor massa, vitae posuere sem tincidunt eget. Duis non
            vestibulum diam. Pellentesque eleifend interdum mollis. Donec
            porttitor dui enim. Maecenas a semper sem. Nunc molestie turpis
            vitae sem auctor, non venenatis velit ultricies.
          </template>
        </accordion-item>

        <accordion-item :item-id="3">
          <template slot="header">Item C</template>
          <template slot="content">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec
            finibus auctor massa, vitae posuere sem tincidunt eget. Duis non
            vestibulum diam. Pellentesque eleifend interdum mollis. Donec
            porttitor dui enim. Maecenas a semper sem. Nunc molestie turpis
            vitae sem auctor, non venenatis velit ultricies.
          </template>
        </accordion-item>
      </accordion-list>
    </div>
  </div>
</template>

<script>
import AccordionList from "./assets/js/components/AccordionList"
import AccordionItem from "./assets/js/components/AccordionItem"

export default {
  name: "App",

  components: { AccordionList, AccordionItem }
}
</script>

<style src="./assets/css/app.css" />
