<template>
	<div class="website-services-marquee">
		<div class="website-services-marquee__container">
		<div class="website-services-marquee__background">
			<div class="website-services-marquee__heading">
			<div class="website-services-marquee__text-container">
				<div class="website-services-marquee__text-wrapper">
				<p class="website-services-marquee__text">
					Website • Domain • Hosting • Email • SEO • Mobile App • Design • VPS • Server • SSL • Responsive • Security • Branding • Marketing • Chatbots • Social Network • Logo • Banner • Trending • UI/UX • Website • Domain • Hosting • Email • SEO • Mobile App • Design • VPS • Server • SSL • Responsive • Security • Branding • Marketing • Chatbots • Social Network • Logo • Banner • Trending • UI/UX • Website • Domain • Hosting • Email • SEO • Mobile App • Design • VPS • Server • SSL • Responsive • Security • Branding • Marketing • Chatbots • Social Network • Logo • Banner • Trending • UI/UX •
				</p>
				</div>
			</div>
			</div>
		</div>
		</div>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'WebsiteServicesMarquee',
});
</script>

<style lang="scss" scoped>
.website-services-marquee {
  width: 105%;
  position: relative;
  left: -2.5%;
  background-color: #c5d4fb;
  background-image: linear-gradient(90deg,#c5d4fb 0,#d6efe8 100%);
  padding: 35px 0;
  transform: rotate(2deg);
  	margin: 34px 0;
    overflow: hidden;

  &__container {
    display: flex;
    justify-content: stretch;
    align-items: stretch;
    flex-wrap: wrap;
    width: 100%;
  }

  &__background {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  &__heading {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  &__text-container {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  &__text-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }

  &__text {
    font-family: 'Inter', sans-serif;
    font-weight: 500;
    font-size: 21.187503814697266px;
    line-height: 1.210227275796216em;
    letter-spacing: 0.04719763162031026em;
    text-align: center;
    color: #000000;
    white-space: nowrap;
    animation: marquee 30s linear infinite; /* Adjust duration as needed */
  }
}

@keyframes marquee {
  0% {
    transform: translateX(0%);
  }
  100% {
    transform: translateX(-25%);
  }
}
</style>
