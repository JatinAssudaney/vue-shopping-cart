<script>
import NavBar from '../components/NavBar.vue'
import ProductItem from '../components/ProductItem.vue'
export default {
  data() {
    return {
      max: 50,
      cart: [],
      displayCart: false,
      products: []
    }
  },
  components: { NavBar, ProductItem },
  created() {
    fetch('https://hplussport.com/api/products/order/price')
      .then(response => response.json())
      .then(data => {
        this.products = data
      })
  },
  computed: {
    filteredProducts() {
      return this.products.filter(item => item.price < this.max)
    },
    cartTotal() {
      return this.cart.reduce((inc, item) => Number(item.price) + inc, 0)
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
      if (this.cartTotal >= 100) {
        this.salesBtn = 'btn-danger'
      }
    }
  }
}
</script>

<template>
  <div>
    <NavBar />
    <section>
      <transition-group name="products" appear>
        <div v-for="item in filteredProducts" :key="item.id" id="item-list">
          <ProductItem :item="item" @add-to-cart="addToCart"></ProductItem>
        </div>
      </transition-group>
    </section>
  </div>
</template>
