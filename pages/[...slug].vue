<script setup>
  const {slug} = useRoute().params;
  console.log(slug);
  const story = await useAsyncStoryblok(
    slug && slug.length > 0 ? slug.join('/'): 'home',
    {version: 'draft'}
  );
</script>
<template>
  <StoryblokComponent v-if="story" :blok="story.content"/>
</template>