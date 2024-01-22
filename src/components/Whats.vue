<template>
    <div>
      <a
        class="whatsapp-button animate-bounce fixed bottom-12 right-12 z-50"
        href="https://api.whatsapp.com/send?phone=556892035878"
        target="_blank"
      >
        <img
          class="w-20 h-20 bg-cover"
          src="/img/whatsapp.png"
          alt="WhatsApp"
        />
      </a>
    </div>
  </template>
  
  <script>
  export default {
    // Seu componente Vue
  };
  </script>
  
  <style scoped>
  .whatsapp-button {
    position: fixed;
  }
  </style>
  