<script>
import { RouterLink, RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
export default {
  data() {
    return {
      cart: [],
      max: 50,
      displayCart: false
    }
  },
  components: { NavBar, RouterLink, RouterView },
  methods: {
    addToCart(product) {
      console.log('🚀 ~ addToCart ~ product:', product)
      this.cart.push(product)
      if (this.cartTotal >= 100) {
        this.salesBtn = 'btn-danger'
      }
    }
  }
}
</script>

<template>
  <div class="flex flex-col p-8 gap-y-8">
    <header>
      <div class="flex items-center justify-between">
        <h1 class="text-4xl"><faIcon icon="shopping-cart" class="mr-2" />Shopping Cart</h1>
        <nav>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/checkout">Checkout</RouterLink>
        </nav>
      </div>
    </header>

    <NavBar :cart="cart" :max="max" />
    <RouterView :cart="cart" :max="max" @addToCart="addToCart" />
  </div>
</template>

<style>
.products-enter-active,
.products-leave-active {
  transition: all 0.5s ease-in-out;
}

.products-enter-from {
  opacity: 0;
  transform: translateX(300px);
}

.products-leave-to {
  opacity: 0;
  transform: translateX(-300px);
}
</style>
