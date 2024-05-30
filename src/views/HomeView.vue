<script>
import ProductItem from '../components/ProductItem.vue'
export default {
  data() {
    return {
      products: []
    }
  },
  props: ['max'],
  components: { ProductItem },
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
    }
  }
}
</script>

<template>
  <div>
    <section>
      <transition-group name="products" appear>
        <div v-for="item in filteredProducts" :key="item.id" id="item-list">
          <ProductItem :item="item"></ProductItem>
        </div>
      </transition-group>
    </section>
  </div>
</template>
