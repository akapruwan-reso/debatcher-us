<script setup lang="ts">
import Navbar from "~/components/layout/navbar.vue";
import Footer from "~/components/layout/footer.vue";
</script>

<template>
  <div class="h-screen">
    <Navbar/>
    <slot/>
    <Footer/>
  </div>
</template>