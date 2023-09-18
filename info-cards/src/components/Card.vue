<script setup>
  const props = defineProps({
    name: String,
    gender: String,
    email: String,
    status: String,
    id: Number,
    image: String,
  })
</script>

<template>
  <div class="w-[70%] h-auto bg-purple-900 text-white rounded-lg flex flex-col">
    <div class="w-full h-auto pb-5 bg-purple-700 text-white rounded-lg">
      <span class="w-full h-44 border-purple-950 rounded-tl-lg rounded-tr-lg border-4 block">
        <img :src="image" alt="User avatar" class="object-cover w-full h-full">
      </span>
      <h1 class="pt-5 pl-5 pr-5 text-3xl break-words">{{ name }}</h1>
      <h2 class="pt-5 pl-5 pr-5 text-2xl first-letter:uppercase italic">{{ gender }}</h2>
      <h3 class="pt-5 pl-5 pr-5 text-lg break-words">{{ email }}</h3>
    </div>
    <h5 class="pb-5 pl-5 pr-5 text-xl"><strong>Status:</strong> {{ status }}</h5>
    <h4 class="pb-5 pl-5 pr-5 text-xl"><strong>ID</strong>: {{ id }}</h4>
  </div>
</template>