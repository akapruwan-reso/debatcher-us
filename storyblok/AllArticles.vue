<template>
  <div class="banner w-full h-[240px] overflow-hidden" v-if="blok.banner !== undefined">
    <img 
            :src="blok.banner.filename + '/m/1920x240/smart'"
            :alt="blok.banner.alt"
            class="aspect-[16/9] w-full bg-gray-100 object-cover sm:aspect-[2/1] lg:aspect-[3/2]"
          />
  </div>
  <div class="bg-white py-4 sm:py-20">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <h2 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">{{ blok.headline }}</h2>
        <p class="mt-2 text-lg leading-8 text-gray-600">{{ blok.tagline }}</p>
      </div>
      <div class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-x-8 gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-3">
        <ArticleCard
          v-for="article in articles"
          :key="article.uuid"
          :article="article.content"
          :date="article.date"
          :slug="article.full_slug"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
  defineProps({ blok: Object });

  const articles = ref(null);
  const storyblokApi = useStoryblokApi();
  const { data } = await storyblokApi.get('cdn/stories', {
    version: 'draft',
    starts_with: 'blog-stories',
    is_startpage: false,
  })
  articles.value = data.stories
  </script>