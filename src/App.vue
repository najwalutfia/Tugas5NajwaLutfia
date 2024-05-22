<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-pink text-white">
      <q-toolbar>
        <q-btn flat dense round icon="" aria-label="Menu" @click="drawer = !drawer"></q-btn>
        <q-toolbar-title>Toko My Cat</q-toolbar-title>
        <q-btn flat dense round icon="" aria-label=""></q-btn>
      </q-toolbar>
    </q-header>



    <!-- Page Container -->
    <q-page-container>
      <q-page class="q-pa-md">

        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          animated
          control-color="white"
          arrow-color="white"
          height="400px"
          class="rounded-borders"
          infinite
          autoplay
          dot-color="primary"
          arrow-size="30px"
        >
          <q-carousel-slide v-for="(image, index) in carouselImages" :key="index" :name="index" :img-src="image.src">
            <div class="absolute-bottom text-subtitle1 text-center text-shadow">
              {{ image.caption }}
            </div>
          </q-carousel-slide>
        </q-carousel>

        <!-- Product Cards -->
        <div class="q-gutter-md q-my-md row justify-around">
          <q-card v-for="(product, index) in products" :key="index" class="my-card">
            <q-img :src="product.image" :alt="product.name" class="my-card-image" />
            <q-card-section>
              <div class="text-h6">{{ product.name }}</div>
              <div class="text-subtitle1">{{ product.price }}</div>
            </q-card-section>
            <q-card-actions>
              <q-btn flat color="primary" @click="addToCart(product)">Add to Cart</q-btn>
            </q-card-actions>
          </q-card>
        </div>

      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer elevated class="bg-pinks-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          Toko My Cat &copy; 2024
        </q-toolbar-title>
        <div>
          Najwa Lutfia Nisya_22350903
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      slide: 0,
      carouselImages: [
        { src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSdtvGuKsWkHiMhBmZpUntkaxxeSK70MErIs5yfNc9WLA&s', caption: 'Welcome to Toko My Cat!' },
        { src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRSm84XEqHbLcRIffPwZ4_27kQqVVkjuYLzXQ&s', caption: 'Best Cat Products' },
        { src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSZj3-iR-S_KUop9uCJAoiiwKKxZmrQMWl51Q&s', caption: 'Special Offers' },
        { src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR24LQP8PER3AJX1qsSglzryxBN3tP5Hev_sg&s', caption: 'Quality Cat Accessories' },
        { src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQPi2qcpjIt95u88VUrY0DwQM5POFgoV3SfVg&s', caption: 'Shop Now!' }
      ],
      products: [
        { image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTGjxu5Gbvd3A8WRLvkBdAukErsAa2stbVnlg&s', name: 'Cat Food', price: 'Rp 35.000' },
        { image: 'https://o-cdn-cas.sirclocdn.com/parenting/images/Mainan_Kucing_Interaktif_Play_Toy.width-800.format-webp.webp', name: 'Cat Toy', price: 'Rp. 26.000' },
        { image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ2uZGZZGSZ7VNdc8F41Muv5vdXS7Fao5bjEg&s', name: 'Cat Bed', price: 'Rp. 50.000' },
        { image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRG6Ue-LvuWwBe1JNM_YdyeyAYsACrKJ-EeuA&s', name: 'Cat Carrier', price: 'Rp. 48.000' }
      ]
    };
  },
  methods: {
    addToCart(product) {
      // Handle adding to cart logic here
      console.log('Added to cart:', product.name);
    }
  }
};
</script>

<style scoped>
.my-card {
  width: 150px;
  max-width: 100%;
}

.my-card-image {
  height: 200px;
}

.q-carousel-slide {
  display: flex;
  align-items: center;
  justify-content: center;
}

.q-carousel-slide .absolute-bottom {
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  padding: 10px;
}

.q-carousel-slide img {
  max-height: 100%;
  width: auto;
}
</style>