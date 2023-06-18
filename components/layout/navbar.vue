<template>
  <header class="bg-white">
    <nav class="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
      <div class="flex lg:flex-1">
        <a href="#" class="-m-1.5 p-1.5">
          <span class="sr-only">OMG Storyblok</span>
        </a>
      </div>
      <div class="flex lg:hidden">
        <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = true">
          <span class="sr-only">Open main menu</span>
          <Bars3Icon class="h-6 w-6" aria-hidden="true" />
        </button>
      </div>
      <div class="hidden lg:flex lg:gap-x-12">
        <a v-for="item in headerMenu" :href="item.link.story.url" class="text-sm font-semibold leading-6 text-gray-900">{{ item.menu_item == ''? link.story.name : item.menu_item }}</a>
      </div>
      <div class="hidden lg:flex lg:flex-1 lg:justify-end">
   
      </div>
    </nav>
  </header>
</template>

<script setup>

const headerMenu = ref(null)

const storyblokApi = useStoryblokApi()
const {data} = await storyblokApi.get('cdn/stories/config', {
  version: 'draft',
  resolve_links: 'url',
})

headerMenu.value = data.story.content.header_menu

</script>