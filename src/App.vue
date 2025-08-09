<script setup>
import TheWelcome from "./components/tes/TesWlcome.vue";
import Navbar from "./components/NavbarItem.vue";
</script>

<template>
  <div class="min-h-screen flex flex-col bg-white dark:bg-black">
    <header>
      <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->
      <Navbar msg="Hello World" />
    </header>

    <main class="flex-1 items-center">
      <TheWelcome msg="Muh. Zulhaji" />
    </main>
  </div>
</template>
