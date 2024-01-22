<template>
  <div class="mb-9">
    <Navbar logo="/img/LOGOS.png"></Navbar>
    <Head></Head>

    <div class="w-[90%] mt-11 mx-auto ">
      <div class="mx-auto bg-blue-300 p-9 mb-11 rounded">
        <h1 class="text-center text-white text-5xl mb-8">
         Bem vindo
        </h1>
        <p class="text-white font-semibold text-2xl leading-7">
          À Encantada, sua loja especializada em laços de cabelo feitos à mão
          com carinho e dedicação. Aqui, cada laço é mais do que um simples
          acessório; é uma pequena obra de arte que adiciona charme e elegância
          ao seu visual. Nossos laços são cuidadosamente produzidos à mão, com
          atenção aos detalhes que fazem toda a diferença. Utilizamos materiais
          de alta qualidade para garantir não apenas a beleza, mas também a
          durabilidade de cada peça.
          Encante-se com a exclusividade da Encantada onde a magia está nos
          detalhes e a elegância é feita à mão, especialmente para você.
        </p>
      </div>
      <div
        class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8"
      >
        <div 
          v-for="(image, index) in catalogImages"
          :key="index"
          class="catalog-item relative overflow-hidden rounded-lg shadow-md"
        >
          <img
            :src="image"
            alt=""
            class="w-full h-80 object-cover rounded-t-lg cursor-pointer"          
          />
          <div class="p-4 bg-pink-200 rounded-b-lg">
            <div class="text-xl font-bold mb-2">Laço {{ index + 1 }}</div>
          </div>
        </div>
      </div>
    </div>
    <Whats></Whats>
    <div v-if="showPopup" class="popup-container" @click="closePopup">
      <div class="popup-content">
        <img
          :src="popupImage"
          alt="Pop-up Image"
          class="w-full h-full object-cover rounded"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import Head from "@/components/Head.vue";
import Whats from "@/components/Whats.vue";
import Navbar from "@/components/Navbar.vue";

let showPopup = false;
let popupImage = "";

const openPopup = (image) => {
  showPopup = true;
  popupImage = image;
};

const closePopup = () => {
  showPopup = false;
  popupImage = "";
};

const catalogImages = [
  "/img/img1.jpg",
  "/img/img2.jpg",
  "/img/img4.jpg",
  "/img/img5.jpg",
  "/img/img8.jpg",
  "/img/img12.jpg",
  "/img/img14.jpg",
  "/img/img15.jpg",
  "/img/img16.jpg",
  "/img/img18.jpg",
  "/img/img19.jpg",
  "/img/img20.jpg",
  "/img/img22.jpg",
  "/img/img23.jpg",
];
</script>

<style scoped>
h1, p {
  font-family: "Sevillana", cursive;
  font-weight: 400;
}

.catalog-item  {
  transition: transform 0.3s ease-in-out;
}

.catalog-item:hover  {
  transform: scale(1.15);
}

@media (max-width: 800px){

  .catalog-item  {
  transition: transform 0.3s ease-in-out;
}

.catalog-item:hover  {
  transform: scale(1.1);
}

}


</style>
