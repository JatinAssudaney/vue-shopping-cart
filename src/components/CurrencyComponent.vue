<template>
  {{ dollar(amt) }}
</template>
<script lang="ts">
export default {
  props: ['amt'],
  methods: {
    dollar(value) {
      return '$' + Number.parseFloat(value).toFixed(2)
    }
  }
}
</script>
