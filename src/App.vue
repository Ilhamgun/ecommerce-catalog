<template>
  <div :class="`container`" :style="bgStyle">
    <div class="card">
      <div v-if="loading" class="loader-overlay">
        <div class="loader"></div>
      </div>

      <template
        v-if="
          product &&
          (product.category === 'men\'s clothing' || product.category === 'women\'s clothing')
        "
      >
        <div class="product" :class="product.category === 'men\'s clothing' ? 'men' : 'women'">
          <img :src="product.image" alt="product" class="product-img" />
          <div class="product-info">
            <div class="product-desc">
              <h2 :class="product.category === 'men\'s clothing' ? 'title-blue' : 'title-purple'">
                {{ product.title }}
              </h2>
              <div class="product-category">
                <p class="category">{{ product.category }}</p>
                <div class="rating">
                  <span>{{ product.rating.rate }}/5</span>
                  <span v-html="getStars(product.rating.rate)"></span>
                </div>
              </div>
              <hr />
              <p class="description">{{ product.description }}</p>
            </div>
            <div class="product-button">
              <hr />
              <div class="price">${{ product.price }}</div>
              <div class="buttons">
                <button :class="product.category === 'men\'s clothing' ? 'btn-blue' : 'btn-purple'">
                  Buy now
                </button>
                <button class="btn-outline" @click="nextProduct">Next product</button>
              </div>
            </div>
          </div>
        </div>
      </template>

      <template v-else>
        <div class="unavailable">
          <img src="/sad-face.png" alt="sad face" class="sad-face" />
          <div class="unavailable-content">
            <p>This product is unavailable to show</p>
            <div class="buttons">
              <button class="btn-outline" @click="nextProduct">Next product</button>
            </div>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      index: 1,
      product: null,
      loading: false,
    }
  },
  computed: {
    bgStyle() {
      if (!this.product) return { '--bg-color': '#dcdcdc' }
      switch (this.product.category) {
        case "men's clothing":
          return { '--bg-color': '#d6e6ff' }
        case "women's clothing":
          return { '--bg-color': '#fde2ff' }
        default:
          return { '--bg-color': '#dcdcdc' }
      }
    },
  },
  methods: {
    async fetchProduct() {
      this.loading = true
      try {
        const res = await fetch(`https://fakestoreapi.com/products/${this.index}`)
        const data = await res.json()
        this.product = data
      } catch (err) {
        console.error('Error fetching product:', err)
        this.product = null
      } finally {
        this.loading = false
      }
    },
    nextProduct() {
      this.index = this.index >= 20 ? 1 : this.index + 1
      this.fetchProduct()
    },
    getStars(rate) {
      const filled = Math.floor(rate)
      const stars = Array.from({ length: 5 }, (_, i) => (i < filled ? '●' : '○'))
      return stars.join(' ')
    },
  },
  mounted() {
    this.fetchProduct()
  },
}
</script>
