<template>
  <div class="accordion-list">
    <slot></slot>
  </div>
</template>

<script>
export default {
  // 'provide' can be an obj or a function which returns an obj.
  // It is used to pass data to all children (no matter how much nested)
  provide() {
    return {
      sharedState: this.sharedState
    }
  },

  // By declaring 'activeItem' as direct property of data, it won't be reactive with provide/inject
  // The solution is to wrap 'activeItem' in an obj which will be automatically treated as reactive with provide/inject https://blog.logrocket.com/how-to-make-provide-inject-reactive/
  data() {
    return {
      sharedState: {
        activeItem: 1
      }
    }
  }
}
</script>
