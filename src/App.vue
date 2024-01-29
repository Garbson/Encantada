<template>
  <div class="mb-9">
    <Head></Head>

    <div class="w-[90%] mt-11 mx-auto">
      <div class="mx-auto bg-blue-300 p-9 mb-11 rounded">
        <h1 class="text-center text-white text-5xl mb-8">Bem vindo</h1>
        <p class="text-white font-semibold text-2xl leading-7">
          À Encantada, sua loja especializada em laços de cabelo feitos à mão
          com carinho e dedicação. Aqui, cada laço é mais do que um simples
          acessório; é uma pequena obra de arte que adiciona charme e elegância
          ao seu visual. Nossos laços são cuidadosamente produzidos à mão, com
          atenção aos detalhes que fazem toda a diferença. Utilizamos materiais
          de alta qualidade para garantir não apenas a beleza, mas também a
          durabilidade de cada peça. Encante-se com a exclusividade da Encantada
          onde a magia está nos detalhes e a elegância é feita à mão,
          especialmente para você.
        </p>
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-8">
  <div
    v-for="(image, index) in catalogImages"
    :key="index"
    class="catalog-item relative overflow-hidden rounded-lg shadow-md"
  >
    <img
      :src="image"
      alt=""
      class="w-full h-96 object-cover rounded-t-lg cursor-pointer"
      @click="toggleImageExpand(index)"
    />
    <div class="p-4 bg-pink-200 rounded-b-lg">
      <div class="text-xl font-bold mb-2">Laço {{ index + 1 }}</div>
      <div class="text-lg font-semibold">
        Preço: {{ catalogPrices[index] }}
      </div>
      <!-- Adicione o botão "Comprar" com o link do WhatsApp -->
      <a :href="getWhatsAppLink(index)" class="btn-comprar">Comprar</a>
    </div>
  </div>
</div>
    <Whats></Whats>

    <!-- Popup Section -->
    <div>
      <div v-if="showPopup" class="section" @click="closePopup">
        <div class="data">
          <!-- Add content for the popup using selectedCatalogItemIndex -->
          <div
            class="catalog-item relative overflow-hidden rounded-lg shadow-md"
          >
            <img
              v-if="selectedCatalogItemIndex !== null && isImageExpanded"
              :src="catalogImages[selectedCatalogItemIndex]"
              alt=""
              class="w-full h-96 object-cover rounded-t-lg cursor-pointer expanded-image"
            />
            <div class="c p-4 bg-pink-200 rounded-b-lg mx-auto w-4/5">
              <!-- Ajuste aqui -->
              <div class="text-xl font-bold mb-2">
                Laço {{ selectedCatalogItemIndex + 1 }}
              </div>
              <div class="text-lg font-semibold">
                Preço: {{ catalogPrices[selectedCatalogItemIndex] }}
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="overlay" v-if="showPopup" @click="closePopup"></div>
    </div>
    <!-- End Popup Section -->
  </div>
  </div>
</template>

<script setup>
import Head from "@/components/Head.vue";
import Whats from "@/components/Whats.vue";
import { ref } from "vue";

const catalogImages = [
  "/img/img1.jpg",
  "/img/img2.jpg",
  "/img/img5.jpg",
  "/img/img8.jpg",
  "/img/img12.jpg",
  "/img/img15.jpg",
  "/img/img16.jpg",
  "/img/img18.jpg",
  "/img/img19.jpg",
  "/img/img20.jpg",
  "/img/img22.jpg",
  "/img/laço1.jpg",
  "/img/laço2.jpg",
  "/img/laço3.jpg",
];

const catalogPrices = [
  "R$15.00",
  "R$10.00",
  "R$20.00",
  "R$13.00",
  "R$15.00",
  "R$15.00",
  "R$8.00",
  "R$40.00 o par",
  "R$20.00 a unidade",
  "R$40.00 o par",
  "R$40.00 o par",
  "R$40.00 o kit",
  "R$25",
  "R$15",

  // ... (outros preços)
];

const showPopup = ref(false);
const selectedCatalogItemIndex = ref(null);
const isImageExpanded = ref(false);

function toggleImageExpand(index) {
  showPopup.value = true;
  selectedCatalogItemIndex.value = index;
  isImageExpanded.value = !isImageExpanded.value;
}

function closePopup() {
  showPopup.value = false;
  selectedCatalogItemIndex.value = null;
  isImageExpanded.value = false;
}
function getWhatsAppLink(index) {
  const numeroWhatsApp = "556892035878"; // Substitua pelo seu número de WhatsApp
  const mensagem = `Olá, estou interessado no Laço ${index + 1}.`;

  return `https://wa.me/${numeroWhatsApp}?text=${encodeURIComponent(mensagem)}`;
}
</script>

<style scoped>
h1,
p {
  font-family: "Sevillana", cursive;
  font-weight: 400;
}

.btn-comprar {
  display: inline-block;
  margin-top: 10px;
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn-comprar:hover {
  background-color: #45a049;
}
.card{
  width: 80%;
}

.catalog-item {
  transition: transform 0.3s ease-in-out;
}

.catalog-item:hover {
  transform: scale(1.05);
}

.expanded-image {
  width: auto;
  height: auto;
  max-width: 80%;
  max-height: 800px;
  display: flex;
  margin: auto auto;
}

.section {
  /* Mantenha as propriedades existentes */
  height: auto;
  width: auto;
  background-color: transparent;
  border-radius: 0; /* Remova o arredondamento */
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  pointer-events: none;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 1;
}

.data {
  /* Mantenha as propriedades existentes */
  background-color: transparent;
}

@media (max-width: 800px) {
  .catalog-item {
    transition: transform 0.3s ease-in-out;
  }

  .catalog-item:hover {
    transform: scale(1.05);
  }
  .section {
    width: 90%; /* ou outra largura desejada */
  }

  .expanded-image {
    max-width: 100%; /* Certifique-se de que a imagem não ultrapasse a largura da tela */
    max-height: 70vh; /* Ajuste conforme necessário */
  }
  
  .c{
    width: 100%;
  }
}
</style>
