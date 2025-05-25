<script setup lang="ts">
import {
	ref,
	onMounted,
	onUnmounted,
	computed,
	defineComponent,
	h,
	StyleValue,
} from "vue";

// Định nghĩa kiểu dữ liệu cho một thẻ
interface CardData {
	id: number;
	title: string;
	content: string;
	Icon: any; // Kiểu dữ liệu cho component Icon
	bgColor: string; // Sẽ là giá trị màu CSS, ví dụ: '#0ea5e9'
	textColor: string; // Sẽ là giá trị màu CSS, ví dụ: '#f0f9ff'
}

// Các thành phần biểu tượng (SVG dưới dạng functional components)
const createIconComponent = (pathData: {
	d?: string;
	paths?: { d: string; fill?: string }[];
	circles?: { cx: string; cy: string; r: string; fill?: string }[];
}) => {
	return defineComponent({
		props: {
			// class prop is removed as styling will be handled by SCSS or direct svg attributes
			width: { type: [String, Number], default: 24 },
			height: { type: [String, Number], default: 24 },
			iconClass: { type: String, default: "" }, // For specific icon styling if needed
		},
		render() {
			const children = [];
			if (pathData.d) {
				children.push(h("path", { d: pathData.d }));
			}
			if (pathData.paths) {
				pathData.paths.forEach((p) =>
					children.push(h("path", { d: p.d, fill: p.fill || "none" }))
				);
			}
			if (pathData.circles) {
				pathData.circles.forEach((c) =>
					children.push(
						h("circle", {
							cx: c.cx,
							cy: c.cy,
							r: c.r,
							fill: c.fill || "currentColor",
						})
					)
				);
			}
			return h(
				"svg",
				{
					xmlns: "http://www.w3.org/2000/svg",
					viewBox: "0 0 24 24",
					fill: "none",
					stroke: "currentColor",
					strokeWidth: "2",
					strokeLinecap: "round",
					strokeLinejoin: "round",
					width: this.width,
					height: this.height,
					class: this.iconClass,
				},
				children
			);
		},
	});
};

const ChevronDown = createIconComponent({ d: "m6 9 6 6 6-6" });
const Newspaper = createIconComponent({
	paths: [
		{
			d: "M4 22h16a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2H8a2 2 0 0 0-2 2v16a2 2 0 0 1-2 2Zm0 0a2 2 0 0 1-2-2V9c0-1.1.9-2 2-2h4v10a2 2 0 0 0 2 2Z",
		},
		{ d: "M18 22V4a2 2 0 0 0-2-2H8a2 2 0 0 0-2 2v16a2 2 0 0 1-2 2Z" },
		{ d: "M10 6h8" },
		{ d: "M10 10h8" },
		{ d: "M10 14h4" },
	],
});
const Palette = createIconComponent({
	circles: [
		{ cx: "13.5", cy: "6.5", r: ".5", fill: "currentColor" },
		{ cx: "17.5", cy: "10.5", r: ".5", fill: "currentColor" },
		{ cx: "8.5", cy: "7.5", r: ".5", fill: "currentColor" },
		{ cx: "6.5", cy: "12.5", r: ".5", fill: "currentColor" },
	],
	paths: [
		{
			d: "M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10c.926 0 1.648-.746 1.648-1.688 0-.437-.18-.835-.437-1.125-.29-.289-.438-.652-.438-1.125a1.64 1.64 0 0 1 1.668-1.668h1.996c3.051 0 5.555-2.503 5.555-5.554C21.965 6.012 17.461 2 12 2z",
		},
	],
});
const Rocket = createIconComponent({
	paths: [
		{
			d: "M4.5 16.5c-1.5 1.26-2 5-2 5s3.74-.5 5-2c.71-.84.7-2.13-.09-2.91a2.18 2.18 0 0 0-2.91-.09z",
		},
		{
			d: "m12 15-3-3a22 22 0 0 1 2-3.95A12.87 12.87 0 0 1 22 2c0 2.72-.78 7.5-6 11a22.35 22.35 0 0 1-4 2z",
		},
		{ d: "M9 12H4s.55-3.03 2-4c1.62-1.08 5 0 5 0" },
		{ d: "M12 15v5s3.03-.55 4-2c1.08-1.62 0-5 0-5" },
	],
});

// Dữ liệu mẫu cho các thẻ
const cardData: CardData[] = [
	{
		id: 1,
		title: "Thẻ Khởi Đầu",
		content:
			"Đây là thẻ đầu tiên, luôn hiển thị ở trên cùng khi bắt đầu và sẽ bị các thẻ khác đè lên.",
		Icon: Newspaper,
		bgColor: "#0ea5e9", // sky-500
		textColor: "#f0f9ff", // sky-50
	},
	{
		id: 2,
		title: "Thẻ Tiếp Theo",
		content:
			"Khi cuộn, thẻ này sẽ được kéo lên từ dưới và đặt chồng lên thẻ trước đó.",
		Icon: Palette,
		bgColor: "#f59e0b", // amber-500
		textColor: "#fffbeb", // amber-50
	},
	{
		id: 3,
		title: "Thẻ Thứ Ba",
		content:
			"Hiệu ứng tiếp tục, thẻ này lại được kéo lên trên cùng, đè lên thẻ thứ hai.",
		Icon: Rocket,
		bgColor: "#10b981", // emerald-500
		textColor: "#ecfdf5", // emerald-50
	},
	{
		id: 4,
		title: "Thẻ Cuối Cùng",
		content:
			"Đây là thẻ cuối cùng trong chuỗi. Nó sẽ được kéo lên và nằm trên tất cả các thẻ khác.",
		Icon: ChevronDown,
		bgColor: "#6366f1", // indigo-500
		textColor: "#eef2ff", // indigo-50
	},
];

const scrollY = ref(0);
const viewportHeight = ref(0);
const containerRef = ref<HTMLElement | null>(null);

const handleScroll = () => {
	scrollY.value = window.scrollY;
};

const updateViewportHeight = () => {
	viewportHeight.value = window.innerHeight;
};

onMounted(() => {
	updateViewportHeight();
	handleScroll();
	window.addEventListener("scroll", handleScroll);
	window.addEventListener("resize", updateViewportHeight);
});

onUnmounted(() => {
	window.removeEventListener("scroll", handleScroll);
	window.removeEventListener("resize", updateViewportHeight);
});

const cardSlotScrollHeight = computed(() => viewportHeight.value * 0.7);

const totalScrollableHeight = computed(() => {
	if (viewportHeight.value === 0) return 0;
	return (
		(cardData.length - 1) * cardSlotScrollHeight.value +
		viewportHeight.value
	);
});

interface CardItemProps {
	card: CardData;
	index: number;
	currentScrollY: number;
	currentViewportHeight: number;
	totalCards: number;
	currentCardSlotScrollHeight: number;
}

const CardItem = defineComponent({
	props: {
		card: { type: Object as () => CardData, required: true },
		index: { type: Number, required: true },
		currentScrollY: { type: Number, required: true },
		currentViewportHeight: { type: Number, required: true },
		totalCards: { type: Number, required: true },
		currentCardSlotScrollHeight: { type: Number, required: true },
	},
	setup(props: CardItemProps) {
		const cardHeight = 360;

		const dynamicStyles = computed(() => {
			const {
				index,
				currentScrollY,
				totalCards,
				currentCardSlotScrollHeight,
			} = props;

			const appearStartScroll = (index - 1) * currentCardSlotScrollHeight;
			let appearProgress =
				(currentScrollY - appearStartScroll) /
				currentCardSlotScrollHeight;
			appearProgress = Math.max(0, Math.min(1, appearProgress));

			const recedeStartScroll = index * currentCardSlotScrollHeight;
			let recedeProgress =
				(currentScrollY - recedeStartScroll) /
				currentCardSlotScrollHeight;
			recedeProgress = Math.max(0, Math.min(1, recedeProgress));

			let opacity = 0;
			let scale = 0.85;
			let translateY = "25px";
			const zIndex = index;

			if (index === 0) {
				opacity = 1 - recedeProgress * 0.6;
				scale = 1 - recedeProgress * 0.1;
				translateY = `${recedeProgress * -20}px`;
				if (currentScrollY < 10) {
					opacity = 1;
					scale = 1;
					translateY = "0px";
				}
			} else if (index < totalCards - 1) {
				if (appearProgress < 1) {
					opacity = appearProgress;
					scale = 0.85 + appearProgress * 0.15;
					translateY = `${25 * (1 - appearProgress)}px`;
				} else {
					opacity = 1 - recedeProgress * 0.6;
					scale = 1 - recedeProgress * 0.1;
					translateY = `${recedeProgress * -20}px`;
				}
			} else {
				opacity = appearProgress;
				scale = 0.85 + appearProgress * 0.15;
				translateY = `${25 * (1 - appearProgress)}px`;
			}

			// Return as StyleValue for Vue's style binding
			const styles: StyleValue = {
				opacity: opacity,
				transform: `scale(${scale}) translateY(${translateY})`,
				zIndex: zIndex,
				backgroundColor: props.card.bgColor,
				color: props.card.textColor,
			};
			return styles;
		});

		return () =>
			h(
				"div",
				{
					style: dynamicStyles.value, // Apply all dynamic styles including colors
					class: "card-item", // SCSS will target this class
				},
				[
					h(
						"div",
						{
							style: { height: `${cardHeight}px` },
							class: "card-item-content-wrapper",
						},
						[
							h("div", {}, [
								h(props.card.Icon, {
									class: "card-icon",
									width: "40",
									height: "40",
								}), // Adjusted icon size
								h(
									"h3",
									{ class: "card-title" },
									props.card.title
								),
								h(
									"p",
									{ class: "card-content-text" },
									props.card.content
								),
							]),
							h(
								"p",
								{ class: "card-footer-text" },
								`Thẻ ${props.index + 1} / ${props.totalCards}`
							),
						]
					),
				]
			);
	},
});
</script>

<template>
	<div class="stacking-cards-app">
		<div class="app-container">
			<div
				v-if="viewportHeight > 0 && totalScrollableHeight > 0"
				ref="containerRef"
				class="cards-container"
				:style="{ height: `${totalScrollableHeight}px` }"
			>
				<CardItem
					v-for="(card, index) in cardData"
					:key="card.id"
					:card="card"
					:index="index"
					:currentScrollY="scrollY"
					:currentViewportHeight="viewportHeight"
					:totalCards="cardData.length"
					:currentCardSlotScrollHeight="cardSlotScrollHeight"
				/>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
// Biến và Mixins (nếu cần)
$slate-900: #0f172a;
$slate-800: #1e293b;
$slate-300: #cbd5e1;
$slate-400: #94a3b8;
$slate-700: #334155;

$sky-400: #38bdf8;
$pink-400: #f472b6;
$amber-400: #fbbf24;

// Responsive breakpoints
$breakpoint-md: 768px;

// Styles chung
body {
	margin: 0;
	font-family: sans-serif; // Tương tự font-sans
}

.stacking-cards-app {
	background-image: linear-gradient(to bottom right, $slate-900, $slate-800);
	min-height: 100vh;
	padding-top: 2.5rem; // py-10
	padding-bottom: 2.5rem; // py-10
	font-family: sans-serif;
}

.app-container {
	margin-left: auto;
	margin-right: auto;
	padding-left: 1rem; // px-4
	padding-right: 1rem; // px-4
	max-width: 48rem; // max-w-3xl (768px)

	@media (min-width: $breakpoint-md) {
		max-width: 48rem; // Tailwind max-w-3xl is 48rem
	}
}

.app-header {
	text-align: center;
	margin-bottom: 3rem; // mb-12
	@media (min-width: $breakpoint-md) {
		margin-bottom: 4rem; // md:mb-16
	}

	.main-title {
		font-size: 2.25rem; // text-4xl
		line-height: 2.5rem;
		font-weight: 700; // font-bold
		color: transparent;
		background-clip: text;
		-webkit-background-clip: text; // Cho Safari
		background-image: linear-gradient(
			to right,
			$sky-400,
			$pink-400,
			$amber-400
		);
		margin-bottom: 1rem; // mb-4

		@media (min-width: $breakpoint-md) {
			font-size: 3rem; // md:text-5xl
			line-height: 1;
		}
	}

	.subtitle {
		font-size: 1.125rem; // text-lg
		line-height: 1.75rem;
		color: $slate-300;
		@media (min-width: $breakpoint-md) {
			font-size: 1.25rem; // md:text-xl
			line-height: 1.75rem;
		}
	}

	.chevron-container {
		margin-top: 2rem; // mt-8
		.chevron-down-icon {
			color: $sky-400;
			margin-left: auto;
			margin-right: auto;
			animation: bounce 1s infinite;
		}
	}
}

@keyframes bounce {
	0%,
	100% {
		transform: translateY(-25%);
		animation-timing-function: cubic-bezier(0.8, 0, 1, 1);
	}
	50% {
		transform: translateY(0);
		animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
	}
}

.cards-container {
	position: relative;
}

.card-item {
	position: sticky;
	top: 0;
	border-radius: 0.75rem; // rounded-xl
	box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25); // shadow-2xl
	padding: 1.5rem; // p-6
	transition-property: opacity, transform;
	transition-duration: 200ms;
	transition-timing-function: ease-out;
	overflow: hidden;

	@media (min-width: $breakpoint-md) {
		padding: 2rem; // md:p-8
	}

	.card-item-content-wrapper {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.card-icon {
		margin-bottom: 1rem; // mb-4
		opacity: 0.8;
		// Kích thước được đặt trực tiếp trong component `h` function
		// width: 2.5rem; height: 2.5rem; // w-10 h-10
		// @media (min-width: $breakpoint-md) {
		//   width: 3rem; height: 3rem; // md:w-12 md:h-12
		// }
	}

	.card-title {
		font-size: 1.5rem; // text-2xl
		line-height: 2rem;
		font-weight: 700;
		margin-bottom: 0.75rem; // mb-3
		@media (min-width: $breakpoint-md) {
			font-size: 1.875rem; // md:text-3xl
			line-height: 2.25rem;
		}
	}

	.card-content-text {
		font-size: 0.875rem; // text-sm
		line-height: 1.25rem;
		line-height: 1.625; // leading-relaxed
		@media (min-width: $breakpoint-md) {
			font-size: 1rem; // md:text-base
			line-height: 1.5rem;
		}
	}

	.card-footer-text {
		font-size: 0.75rem; // text-xs
		line-height: 1rem;
		opacity: 0.7;
		margin-top: 1rem; // mt-4
	}
}

.loading-message {
	text-align: center;
	color: $slate-400;
	padding: 2.5rem;
}

.app-footer {
	text-align: center;
	margin-top: 5rem; // mt-20
	padding-top: 2.5rem; // py-10
	padding-bottom: 2.5rem; // py-10
	border-top: 1px solid $slate-700;
	p {
		color: $slate-400;
	}
}
</style>

