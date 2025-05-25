<script setup lang="ts">
import { ref, onMounted, onUnmounted, computed, CSSProperties } from "vue";

interface Feature {
	title: string;
	description: string;
	image: string;
}

const features: Feature[] = [
	{
		title: "Built for Speed. Made to Last.",
		description:
			"Launch and host websites that run like a dream with super fast hosting and industry leading infrastructure that is top ranked by Google's Core Web Vitals.",
		image: "https://elementor.com/cdn-cgi/image/f=auto,w=1172/https://elementor.com/wp-content/uploads/2024/06/Frame-10886828-min.webp",
	},
	{
		title: "Scalable Hosting For Any Business",
		description:
			"Tough enough to handle the heaviest traffic spikes and surges, Elementor hosting keeps your website up and running 24/7, 365 days a year so that you can grow without limits.",
		image: "https://elementor.com/cdn-cgi/image/f=auto,w=1204/https://elementor.com/wp-content/uploads/2024/06/Frame-10886731-min.png",
	},
	{
		title: "Ironclad Security You Can Depend On.",
		description:
			"With Elementor hosting your websites get enterprise grade security that's monitored by cyber experts to ensure a smooth, safe and secure online experience for you and your site visitors.",
		image: "https://elementor.com/cdn-cgi/image/f=auto,w=1354/https://elementor.com/wp-content/uploads/2024/06/Frame-10886830-min.png",
	},
];

const sectionRef = ref<HTMLElement | null>(null);
const featuresStickyWrapperRef = ref<HTMLElement | null>(null);

const scrollYPos = ref(0);
const viewportHeight = ref(0);
const sectionoffsetTop = ref(0);
const totalAnimationScrollHeight = ref(0);

// Configuration Constants
const SCROLL_NEEDED_PER_CARD_VH = 0.6; // Each card needs 60vh of scroll to transition
const CARD_VP_OCCUPANCY_FACTOR = 0.75; // Affects card travel distance relative to sticky wrapper height

const updateScrollAndViewportMetrics = () => {
	viewportHeight.value = window.innerHeight;
	if (sectionRef.value) {
		sectionoffsetTop.value = sectionRef.value.offsetTop;
	}
	// Total scroll height over which the card animations will occur
	totalAnimationScrollHeight.value =
		features.length * SCROLL_NEEDED_PER_CARD_VH * viewportHeight.value;
};

const handlePageScroll = () => {
	scrollYPos.value = window.pageYOffset;
};

onMounted(() => {
	updateScrollAndViewportMetrics();
	handlePageScroll(); // Initial values
	window.addEventListener("scroll", handlePageScroll);
	window.addEventListener("resize", updateScrollAndViewportMetrics);
});

onUnmounted(() => {
	window.removeEventListener("scroll", handlePageScroll);
	window.removeEventListener("resize", updateScrollAndViewportMetrics);
});

// scrollProgress: 0 to 1 as user scrolls through the designated animation height
const scrollProgress = computed(() => {
	if (totalAnimationScrollHeight.value === 0) return 0;
	const currentScrollWithinAnimation =
		scrollYPos.value - sectionoffsetTop.value;
	return Math.min(
		1,
		Math.max(
			0,
			currentScrollWithinAnimation / totalAnimationScrollHeight.value
		)
	);
});

// Height for the scrollable area on the right, allowing sticky wrapper to travel
const featuresScrollContainerHeight = computed(() => {
	// Ensure enough space for the last card to complete its animation within the sticky wrapper
	return (
		totalAnimationScrollHeight.value +
		viewportHeight.value * (1 - SCROLL_NEEDED_PER_CARD_VH)
	);
});

const calculateCardStyle = (index: number): CSSProperties => {
	const cardDisplayAreaHeight =
		featuresStickyWrapperRef.value?.offsetHeight || viewportHeight.value;

	// normalizedScrollPosition: Advances from 0 to features.length as scrollProgress goes 0 to 1
	const normalizedScrollPosition = scrollProgress.value * features.length;

	// positionRelativeToFocus: 0 when card `index` is in focus.
	// Negative if card `index` has passed focus, positive if upcoming.
	const positionRelativeToFocus = index - normalizedScrollPosition;

	// translateY: Card moves from bottom to top. 0 when focused.
	const translateY =
		positionRelativeToFocus *
		cardDisplayAreaHeight *
		CARD_VP_OCCUPANCY_FACTOR;

	// Opacity: Full opacity when near focus, fades otherwise.
	const focusProximity = Math.abs(positionRelativeToFocus);
	let opacity = 0;
	const halfFocusSlot = 0.5; // Card is fully visible for 0.5 units of focusProximity on each side
	const fadeZone = 0.5; // Additional 0.5 units for fading in/out

	if (focusProximity < halfFocusSlot) {
		opacity = 1;
	} else if (focusProximity < halfFocusSlot + fadeZone) {
		opacity = 1 - (focusProximity - halfFocusSlot) / fadeZone;
	}
	opacity = Math.max(0, Math.min(1, opacity));

	// Scale: Slightly smaller when not directly in focus.
	const scaleFactor = 1 - Math.min(0.05, focusProximity * 0.05); // Max 5% shrink

	return {
		transform: `translateY(${translateY}px) scale(${scaleFactor})`,
		opacity: opacity,
		// Higher zIndex for cards closer to focus
		zIndex: features.length - Math.floor(focusProximity),
	};
};
</script>

<template>
	<section class="elementor-hosting-section" ref="sectionRef">
		<div class="text-content-wrapper">
			<div class="text-content">
				<h2 class="title">
					Hosting that Handles Traffic Spikes with Ease
				</h2>
				<p class="description">
					Lightning fast and tested to the max, Elementor's secure
					managed hosting provides the power and flexibility you need
					to automatically handle any sale or traffic peak,
					accelerating your website to top WordPress hosting
					performance.
				</p>
				<button class="cta-button">Get Started</button>
			</div>
		</div>

		<div
			class="features-scroll-container"
			:style="{ height: `${featuresScrollContainerHeight}px` }"
		>
			<div class="features-sticky-wrapper" ref="featuresStickyWrapperRef">
				<div
					v-for="(feature, index) in features"
					:key="feature.title"
					class="feature-card"
					:style="calculateCardStyle(index)"
				>
					<div class="card-text-area">
						<h3 class="card-title">{{ feature.title }}</h3>
						<p class="card-description">
							{{ feature.description }}
						</p>
					</div>
					<div class="card-image-area">
						<img
							:src="feature.image"
							:alt="feature.title"
							class="card-image"
						/>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<style scoped lang="scss">
.elementor-hosting-section {
	display: flex;
	position: relative;
	background-color: #fff; // Assuming a white page background
	font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
	overflow-x: hidden; // Prevent horizontal scrollbars from slight overflow of cards during animation
}

.text-content-wrapper {
	width: 40%;
	height: 100vh;
	position: sticky;
	top: 0;
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 0 5%; // Adjust padding as needed
	box-sizing: border-box;
}

.text-content {
	max-width: 450px; // Limit width of text block
	.title {
		font-size: 2.8rem; // Approx 44px
		font-weight: 700;
		line-height: 1.2;
		margin-bottom: 24px;
		color: #1a202c; // Dark gray
	}
	.description {
		font-size: 1.1rem; // Approx 18px
		line-height: 1.6;
		margin-bottom: 32px;
		color: #4a5568; // Medium gray
	}
	.cta-button {
		background-color: #e6007e; // Elementor Magenta
		color: white;
		border: none;
		padding: 16px 32px;
		font-size: 1rem;
		font-weight: 600;
		border-radius: 8px;
		cursor: pointer;
		transition: background-color 0.3s ease;
		&:hover {
			background-color: #c00069; // Darker magenta
		}
	}
}

.features-scroll-container {
	width: 60%;
	position: relative;
}

.features-sticky-wrapper {
	height: 100vh;
	position: sticky;
	top: 0;
	background-color: #f5f7ff; // Light lavender-blue background for cards area
	display: flex;
	align-items: center;
	justify-content: center;
	overflow: hidden; // Clip cards that animate outside this box
}

.feature-card {
	position: absolute;
	background-color: white;
	border-radius: 16px;
	box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	padding: 32px;
	display: flex;
	flex-direction: column;
	width: calc(100% - 120px); // Card width relative to wrapper, with padding
	max-width: 600px; // Max card width
	min-height: 400px; // Ensure card has some min height
	box-sizing: border-box;
	transition: transform 0.4s cubic-bezier(0.25, 0.8, 0.25, 1),
		opacity 0.4s ease-out; // Smooth transitions

	.card-text-area {
		margin-bottom: 24px;
		.card-title {
			font-size: 1.75rem; // Approx 28px
			font-weight: 600;
			color: #1a202c;
			margin-bottom: 12px;
		}
		.card-description {
			font-size: 1rem; // Approx 16px
			line-height: 1.6;
			color: #4a5568;
		}
	}

	.card-image-area {
		margin-top: auto; // Pushes image to the bottom if card flex grows
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: flex-end; // Align image to bottom of its area
		img.card-image {
			max-width: 100%;
			height: auto;
			border-radius: 8px;
			object-fit: cover; // Ensure image covers its space well
		}
	}
}

// Responsive adjustments
@media (max-width: 1024px) {
	.elementor-hosting-section {
		flex-direction: column;
	}
	.text-content-wrapper {
		width: 100%;
		position: relative; // No longer sticky like this
		height: auto;
		padding: 40px 20px;
		text-align: center;
	}
	.features-scroll-container {
		width: 100%;
		// Height might need dynamic adjustment or be content-based on mobile
		// For simplicity, animation might behave differently or be less pronounced.
	}
	.features-sticky-wrapper {
		// On mobile, the sticky wrapper might not be 100vh or might need to behave differently
		// For now, it might just stack the cards or show one at a time.
		// This example keeps the animation, but it might be too much for small screens.
		padding: 20px 0; // Add some padding for cards if wrapper isn't full height
	}
	.feature-card {
		width: calc(100% - 40px); // Adjust card width for smaller screens
		padding: 24px;
		min-height: 350px;
		.card-title {
			font-size: 1.5rem;
		}
		.card-description {
			font-size: 0.9rem;
		}
	}
}

@media (max-width: 767px) {
	.text-content .title {
		font-size: 2rem;
	}
	.text-content .description {
		font-size: 1rem;
	}
	.feature-card {
		// Further adjustments if needed for very small screens
		// The animation might become problematic on small screens, might need simplification or disabling.
		// For this example, the animation logic remains.
	}
}
</style>
