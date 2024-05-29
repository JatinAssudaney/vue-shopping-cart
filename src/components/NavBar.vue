<template>
  <nav class="flex flex-col">
    <div class="flex justify-between items-center relative">
      <div class="flex gap-x-4">
        <label for="max-price" class="text-2xl">Max Price (${{ max }})</label>
        <div class="bg-green-700 rounded-full py-0.5 px-2">
          <span class="align-middle text-white text-sm"
            >results: {{ filteredProducts.length }}</span
          >
        </div>
      </div>
      <div v-if="cart.length" class="absolute top-0 right-0">
        <div class="flex flex-col items-end">
          <div class="flex items-center gap-x-3">
            <span class="font-bold bg-white"
              ><CurrencyComponent :amt="cartTotal"></CurrencyComponent
            ></span>
            <button
              @click="displayCart = !displayCart"
              class="flex items-center text-white bg-green-700 px-2 py-1 rounded gap-x-2"
              id="cartDropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              <faIcon icon="shopping-cart" class="text-white"></faIcon>
              <span>{{ cart.length }}</span>
            </button>
          </div>
          <div class="overflow-hidden">
            <transition name="dropdown">
              <div v-if="displayCart" class="flex flex-col rounded" aria-labelledby="cartDropdown">
                <div
                  v-for="(item, index) in cart"
                  :key="index"
                  class="relative bg-white flex items-center justify-between px-2 py-1 border"
                >
                  <div :title="item.name" class="max-w-32 truncate">{{ item.name }}</div>
                  <div class="ml-3 font-weight-bold">
                    <CurrencyComponent :amt="item.price"></CurrencyComponent>
                  </div>
                </div>
              </div>
            </transition>
          </div>
        </div>
      </div>
    </div>
    <input v-model.number="max" type="range" class="form-range" min="0" max="130" />
  </nav>
</template>
<script>
export default {
  props: ''
}
</script>
<style lang=""></style>
