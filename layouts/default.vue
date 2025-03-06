<template>
    <header class= "flex flex-row w-full items-center bg-green-400 border-b-2 border-gray-400 max-sm:justify-between relative">
      <div class = "basis-1/4 items-center justify-start px-8 min-w-40 max-sm:basis-auto">
        <img src="assets/images/logo.jpg" class = "w-16 h-16 bg-transparent">
      </div>
      <div class = "basis-1/4 max-sm:basis-auto">
      </div>
      <nav :class = "{'basis-1/2 flex flex-row items-center justify-end px-8 gap-4': !burger ||burger,
       'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-white max-sm:px-0':burger,
        'max-sm:hidden': !burger,}">
        <NuxtLink to = "/" class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">Home</NuxtLink>
        <div @click="switch_submenu" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-cm:border-b-2 max-sm:border-black max-sm:text-center">Labs
          <div class="flex flex-col absolute top-16 bg-white text-black w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-red-100" v-show="submenu">
            <NuxtLink to = "/Labs" class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">Lab3</NuxtLink>
            <NuxtLink to = "/login" class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">Lab4</NuxtLink>
            <NuxtLink to = "/login" class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">Lab5</NuxtLink>
            <NuxtLink to = "/login" class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">Lab6</NuxtLink>
          </div>
        </div>
        <NuxtLink to = "/login" :class = "{'my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center':submenu,
        'my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-t-2 max-sm:border-black max-sm:text-center':!submenu}">logIn</NuxtLink>
        <NuxtLink to = "/logout" class = "my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">LogOut</Nuxtlink>
      </nav>
      <div v-if="!burger" @click="switch_burger" class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
        <span class="h-[3px] w-full bg-black"></span>
        <span class="h-[3px] w-full bg-black"></span>
        <span class="h-[3px] w-full bg-black"></span>
      </div>
      <div v-else class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
        <span class="h-[3px] w-full bg-black"></span>
        <span class="h-[3px] w-full bg-black"></span>
        <span class="h-[3px] w-full bg-black"></span>
      </div>

    </header>


  <main class="p-5 flex bg-green-100 h-screen">
    <slot/>
  </main>

  <footer class="flex flex-row w-full bg-green-400 border-t-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
    <a href="https://youtube.com"><img src="https://commons.wikimedia.org/wiki/File:YouTube_social_white_square_(2017).svg" class="w-16 h-16"></a>
    <a href="https://github.com"><img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" class="w-16 h-16"></a>
    <a href="https://facebook.com"><img src="https://upload.wikimedia.org/wikipedia/commons/b/b9/2023_Facebook_icon.svg" class="w-16 h-16"></a>
  </footer>

</template>
<script setup lang="ts">
import {useHead} from '#app';
import {ref} from 'vue'

useHead({
  script: [
    {
      async: true,
      src: "https://www.googletagmanager.com/gtag/js?id=G-971TZRKCXE",
    },
    {
      innerHTML: `
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', "G-971TZRKCXE");`
      ,
      type:"text/javascript",
    },
  ],
  __dangerouslyDisableSanitizersByTagID: {
    gtag: [`innerHTML`],
  }
});

const burger = ref<boolean>(false)
const submenu = ref<boolean>(false)

const switch_burger = ()=> {burger.value = !burger.value}
const switch_submenu = ()=>{submenu.value = !submenu.value}
</script>