<script setup lang="ts">
import DemoStackingCards from "./components/DemoStackingCards.vue";
import ElementorHostingSection from "./components/ElementorHostingSection.vue";
import MauWebsiteHero from "./components/MauWebsiteHero.vue";
import MobioNavigation from "./components/MobioNavigation.vue";
import MobioSection from "./components/MobioSection.vue";
import CanhcamServicesSection from "./components/CanhcamServicesSection.vue";
import SimplePageGallery from "./components/SimplePageGallery.vue";
// import MonaTopMenu from "./components/MonaTopMenu.vue";
import SimplePageHero from "./components/SimplePageHero.vue";
import MyPageFeatures from "./components/MyPageFeatures.vue";
import CanhCamStatistics from "./components/CanhCamStatistics.vue";
import SEONgonStatistics from "./components/SEONgonStatistics.vue";
import AWebsiteWorkflow from "./components/AWebsiteWorkflow.vue";
// import ThuyThuTopMenu from "./components/ThuyThuTopMenu.vue";
</script>

<template>
	<div class="app">
		<!-- <MonaTopMenu /> -->

		<!-- <h1 class="section-title">Hero Section - SimplePage</h1>
    <SimplePageHero />
    
    <h1 class="section-title">Hero Section - MauWebsite</h1>
    <MauWebsiteHero /> -->
	<!-- <MobioSection />
	<MyPageFeatures />
	 	<DemoStackingCards />
		<CanhcamServicesSection /> -->
		<SEONgonStatistics />
		<CanhCamStatistics />
		<AWebsiteWorkflow />
	</div>
</template>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
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
