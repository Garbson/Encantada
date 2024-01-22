<template>
  <div class="relative h-screen">
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Kdam+Thmor+Pro&family=Oswald:wght@200&family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Sevillana&display=swap"
      rel="stylesheet"
    />

    <div class="absolute inset-0 bg-black opacity-10 z-10 h-full"></div>
    <!-- Fundo com opacidade -->
    <q-carousel
      animated
      v-model="slide"
      navigation
      infinite
      height="100%"
      :autoplay="autoplay"
      transition-prev="slide-right"
      transition-next="slide-left"
    >
      <q-carousel-slide :name="1" img-src="/img/bg1.jpg" />
      <q-carousel-slide :name="2" img-src="/img/bg3.jpg" />
      <q-carousel-slide :name="3" img-src="/img/bg4.jpg" />
      <q-carousel-slide :name="4" img-src="/img/bg5.jpg" />
    </q-carousel>

    <div
      class="a absolute inset-0 flex items-center justify-center text-white  z-20"
    >
      Encantada
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    return {
      slide: ref(1),
      autoplay: ref(true),
    };
  },
};
</script>

<style scoped>
.a {
  font-family: "Sevillana", cursive;
  font-size: 500%;
  font-weight: 400;
  font-style: normal;
}
</style>
