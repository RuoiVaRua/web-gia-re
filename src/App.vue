<script setup lang="ts">
import SimplePageHero from './components/SimplePageHero.vue';
import MauWebsiteHero from './components/MauWebsiteHero.vue';
</script>

<template>
  <div class="app">
    <h1 class="section-title">Hero Section - SimplePage</h1>
    <SimplePageHero />
    
    <h1 class="section-title">Hero Section - MauWebsite</h1>
    <MauWebsiteHero />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
  background-color: #f5f5f5;
}

.app {
  width: 100%;
}

.section-title {
  text-align: center;
  padding: 40px 0;
  background-color: #333;
  color: white;
  margin: 0;
}
</style>
