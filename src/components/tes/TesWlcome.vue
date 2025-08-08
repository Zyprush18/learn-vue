<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>
<template>
  <section id="home" class="px-10 m-8">
    <div class="flex">
      <div class="p-5 my-10 text-black dark:text-white ">
        <h1 class="text-3xl font-bold pb-3">Hallo, My Name is {{ msg }}</h1>
        <p class=" text-xl">
          a software developer that focuses on developing backend.
        </p>
      </div>
    </div>
  </section>
</template>
