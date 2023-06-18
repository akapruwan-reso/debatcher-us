<template>
  <NuxtLink 
    :to="'/' + slug"
  >
    <article class="flex flex-col items-start justify-between">
    <div class="relative w-full">
      <div v-if="article.image !== undefined">
        <img 
            :src="article.image.filename + '/m/600x0'"
            :alt="article.image.alt"
            class="aspect-[16/9] w-full rounded-2xl bg-gray-100 object-cover sm:aspect-[2/1] lg:aspect-[3/2]"
          />
      </div> 
      <div class="absolute inset-0 rounded-2xl ring-1 ring-inset ring-gray-900/10" />
    </div>
    <div class="max-w-xl">
      <div class="mt-8 flex items-center gap-x-4 text-xs">
        <time  class="text-gray-500">{{ date }}</time>
      </div>
      <div class="group relative">
        <h3 class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600">
          {{ article.title }}
        </h3>
        <p class="mt-5 line-clamp-3 text-sm leading-6 text-gray-600">{{ article.summary }}</p>
      </div>
      <div class="relative mt-8 flex items-center gap-x-4">
        
        <div class="text-sm leading-6">
          <p class="font-semibold text-gray-900">
            {{ article.author }}
          </p>
        </div>
      </div>
    </div>
  </article>
  </NuxtLink>
  
</template>

<script setup>
  defineProps({article: Object, slug: String, date: String})
</script>