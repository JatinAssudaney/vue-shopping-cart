<template>
  <div class="flex items-center justify-between rounded bg-red-200 w-full p-8" role="alert">
    <div class="text-[#721c24]">
      <slot>Congrats on getting some items in your cart.</slot>
    </div>
    <button
      v-if="close"
      @click="closeButton"
      type="button"
      class="text-gray-600 text-2xl"
      aria-label="Close"
    >
      X
    </button>
  </div>
</template>
<script>
export default {
  props: ['close'],
  methods: {
    closeButton() {
      event.target.parentNode.remove()
    }
  }
}
</script>
