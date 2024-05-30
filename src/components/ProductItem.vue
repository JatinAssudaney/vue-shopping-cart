<template>
  <div class="flex">
    <img class="w-1/3" :src="item.image" :alt="item.name" />
    <div class="w-2/3 flex flex-col justify-around">
      <div class="flex flex-col gap-y-3">
        <h3 class="text-blue-500 text-3xl">{{ item.name }}</h3>
        <p class="font-medium">{{ item.description }}</p>
      </div>
      <div>
        <span>Price: </span
        ><span class="font-semibold"
          ><CurrencyComponent :amt="item.price"></CurrencyComponent
        ></span>
      </div>
      <button
        @click="$parent.$parent.$emit('addToCart', item)"
        class="text-white bg-green-700 px-2 py-1 rounded"
      >
        Add to Cart
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import CurrencyComponent from './CurrencyComponent.vue'
export default {
  props: ['item'],
  emits: ['addToCart'],
  components: { CurrencyComponent }
}
</script>
