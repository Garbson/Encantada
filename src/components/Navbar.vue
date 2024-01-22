<template>
    <header :class="[navClass]" class="fixed flex flex-wrap z-50 w-full text-sm py-2">
      <nav class="max-w-[85rem] justify-center flex w-full mx-auto px-4 sm:flex sm:items-center" aria-label="Global">
        <!-- logo -->
        <div class="flex items-center justify-between">
          <a class="flex-none text-xl font-semibold" href="/"> <img :src="logo" alt="" class="h-24" /></a>
        </div>
  
        <!-- nav-bar -->
        <div class="flex-grow">
          <div class="flex gap-5 mt-5 sm:justify-center md:justify-end sm:mt-0 sm:ps-5 centralizar">
            <a class="a  text-xl text-blue-300"  href="https://api.whatsapp.com/send?phone=556892035878" aria-current="page">Faça seu pedido!</a> 
          </div>
        </div>
      </nav>
    </header>
  </template>
  
  <script setup>
  import { onBeforeUnmount, onMounted, ref } from 'vue'
  
  defineProps({
    logo: String
  })
  
  const navClass = ref('bg-green-900')
  
  const updateVisibility = () => {
    navClass.value = window.scrollY > 200 ? 'bg-pink-200' : 'bg-transparent'
  }
  
  onMounted(() => {
    updateVisibility()
    window.addEventListener('scroll', () => {
      updateVisibility()
    })
  })
  
  onBeforeUnmount(() => {
    window.removeEventListener('scroll', () => {
      updateVisibility()
    })
  })
  </script>
  
  <style>
  @media (max-width: 800px) {
    .centralizar {
      justify-content: center;
      gap: 2.15rem;
    }
  }
  .a {
  font-family: "Sevillana", cursive;
  font-weight: 400;
  font-style: italic;
  font-size: x-large;
}
  </style>