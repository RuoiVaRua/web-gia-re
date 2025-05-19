<template>
	<section class="simplepage-hero">
		<div class="background-overlay"></div>
		<div class="container">
			<div class="hero-content">
				<h1 class="heading-title">Simple Page</h1>
				<h2 class="subtitle">
					Nền Tảng Thiết Kế Landing Page Chuyên Nghiệp
				</h2>
				<ul class="icon-list">
					<li>
						<i class="icon-check"></i>Tạo Landing Page chỉ với thao
						tác kéo - thả
					</li>
					<li>
						<i class="icon-check"></i>Không cần biết kiến thức lập
						trình
					</li>
					<li>
						<i class="icon-check"></i>Hơn 1000+ mẫu giao diện có sẵn
					</li>
					<li>
						<i class="icon-check"></i>Miễn phí tên miền & hosting
						chất lượng cao
					</li>
				</ul>
				<a href="#" class="btn-primary animated">Bắt đầu miễn phí</a>
			</div>
			<div class="hero-image-container">
				<div class="">
					<img
						width="580"
						height="326"
						src="https://simpleweb.sgp1.digitaloceanspaces.com/wp-content/uploads/2023/09/banner-simplepage.png"
						alt="banner simplepage"
					/>
				</div>
				<div class="hero-image-wrapper" style="left: 50px; bottom: 110px;">
					<img
						class="hero-image-front"
						width="252"
						height="300"
						src="https://simpleweb.sgp1.digitaloceanspaces.com/wp-content/uploads/2023/09/new-lead.jpeg"
						alt=""
					/>
				</div>
				<div class="hero-image-wrapper" style="right: 40px; bottom: 85px; text-align: right;">
					<img
						class="hero-image-front"
						width="300"
						height="169"
						src="https://simpleweb.sgp1.digitaloceanspaces.com/wp-content/uploads/2023/09/TYLECHUYENDOI.png"
						alt=""
					/>
				</div>
				<div class="hero-image-wrapper hero-image-hover" style="right: 100px; top: 0px; width: 150px;">
					<img src="../assets/custom-domain.svg" alt="" style="width: 100%;" />
				</div>
				<div class="hero-image-wrapper hero-image-beat" style="left: 72px; top: 0px; width: 60px;">
					<img src="../assets/96-page-speed.svg" alt="" style="width: 100%;" />
				</div>
			</div>
		</div>
		<div class="ux-shape-divider">
			<img src="../assets/hero-line.svg" alt="" style="width: 100%; height: 100%;" />
		</div>
	</section>
</template>

<script lang="ts">
export default {
	name: "SimplePageHero",
	mounted() {
		// Add some simple animation when component mounts
		setTimeout(() => {
			const animatedElements = document.querySelectorAll(".animated");
			animatedElements.forEach((el) => {
				el.classList.add("active");
			});
		}, 300);

		// Parallax effect for hero-image-front
		const heroSection = document.querySelector(".simplepage-hero");
		const heroImages = document.querySelectorAll<HTMLImageElement>(".hero-image-front");

		if (heroSection && heroImages.length) {
			heroSection.addEventListener("mousemove", (event) => {
				const e = event as MouseEvent;
				const rect = (e.currentTarget as HTMLElement).getBoundingClientRect();
				const x = e.clientX - rect.left;
				const y = e.clientY - rect.top;
				const centerX = rect.width / 2;
				const centerY = rect.height / 2;
				// Tính dịch chuyển cùng hướng chuột, tối đa 20px
				const maxMove = 10;
				const moveX = ((x - centerX) / centerX) * maxMove;
				const moveY = ((y - centerY) / centerY) * maxMove;
				heroImages.forEach((img) => {
					img.style.transform = `matrix(1, 0, 0, 1, ${moveX}, ${moveY})`;
				});
			});
			// heroSection.addEventListener("mouseleave", () => {
			// 	heroImages.forEach((img) => {
			// 		img.style.transform = "matrix(1, 0, 0, 1, 0, 0)";
			// 	});
			// });
		}
	},
};
</script>

<style scoped lang="scss">
$color_1: #fff;
$color_2: white;
$color_3: #333;
$color_4: #ff8008;
$font-family_1: "Arial", sans-serif;
$background-color_1: #6a1b9a;
$background-color_2: #4a148c;
$background-color_3: white;

/* Animation keyframes */
@keyframes fadeIn {
	from {
		opacity: 0;
	}
	to {
		opacity: 1;
	}
}
@keyframes slideUp {
	from {
		opacity: 0;
		transform: translateY(50px);
	}
	to {
		opacity: 1;
		transform: translateY(0);
	}
}
@keyframes bounce {
	0%,
	20%,
	50%,
	80%,
	100% {
		transform: translateY(0);
	}
	40% {
		transform: translateY(-20px);
	}
	60% {
		transform: translateY(-10px);
	}
}
/* Responsive adjustments */
.simplepage-hero {
	position: relative;
	min-height: 100vh;
	padding: 60px 0 0;
	font-family: $font-family_1;
	background: linear-gradient(135deg, #ff8008 0%, #ffc837 100%);
	overflow: hidden;
	color: $color_1;

	display: flex;
	flex-direction: column;
	justify-content: space-between;
}
.background-overlay {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-image: url("data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAYABgAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjL/wAARCAABAAEDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD3+iiigD//2Q==");
	background-size: cover;
	opacity: 0.1;
	z-index: 0;
}
.container {
	max-width: 1200px;
	margin: 0 auto;
	padding: 0 15px;
	display: flex;
	align-items: center;
	position: relative;
	z-index: 1;
}
.hero-content {
	flex: 1;
	padding-right: 30px;
}
.heading-title {
	font-size: 54px;
	margin-bottom: 10px;
	color: $color_1;
	font-weight: 700;
}
.subtitle {
	font-size: 28px;
	color: $color_1;
	margin-bottom: 30px;
	font-weight: 500;
}
.icon-list {
	list-style: none;
	padding: 0;
	margin-bottom: 35px;
	li {
		margin-bottom: 12px;
		font-size: 18px;
		color: $color_1;
		position: relative;
		padding-left: 30px;
	}
}
.icon-check {
	&::before {
		content: "✓";
		position: absolute;
		left: 0;
		color: $color_1;
		font-weight: bold;
	}
}
.btn-primary {
	display: inline-block;
	background-color: $background-color_1;
	color: $color_2;
	padding: 15px 30px;
	text-decoration: none;
	border-radius: 30px;
	font-size: 18px;
	font-weight: 600;
	transition: all 0.3s ease;
	border: none;
	cursor: pointer;
	box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
	&:hover {
		background-color: $background-color_2;
		transform: translateY(-3px);
		box-shadow: 0 7px 15px rgba(0, 0, 0, 0.3);
	}
}
.hero-image-container {
	flex: 1;
	position: relative;
	padding: 20px;
}
.hero-image-wrapper {
	position: absolute;
	border-radius: 6px;
}
.hero-image-hover {
	transition: transform 0.3s ease;
	animation: drip_down 1s ease 0.5s;
	&:hover {
		transform: scale(1.1);
	}

	@keyframes drip_down {
		0% {
			transform: translateY(0);
		}
		20% {
			transform: translateY(-20px);
		}
		40% {
			transform: translateY(10px);
		}
		60% {
			transform: translateY(-5px);
		}
		80% {
			transform: translateY(2px);
		}
		100% {
			transform: translateY(0);
		}
	}
}
.hero-image-beat {
	animation: beat 1s ease 0.5s;
	@keyframes beat {
		0% {
			transform: scale(1);
		}
		20% {
			transform: scale(1.2);
		}
		40% {
			transform: scale(0.9);
		}
		60% {
			transform: scale(1.05);
		}
		80% {
			transform: scale(0.97);
		}
		100% {
			transform: scale(1);
		}
	}
}
.hero-image-front {
	width: 25%;
	border-radius: 10px;
	height: auto;
	object-fit: contain;
	opacity: 0;
	animation: show 1s linear 1s forwards;

	@keyframes show {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}
}
.hero-banner {
	max-width: 100%;
	height: auto;
	position: relative;
	z-index: 1;
	border-radius: 8px;
	// box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}
.circle-element {
	position: absolute;
	top: 15%;
	right: 5%;
	z-index: 3;
	opacity: 0;
	transform: scale(0.8);
	transition: all 0.7s ease;
}
.circle-element.active {
	opacity: 1;
	transform: scale(1);
}
.trusted-by {
	margin-top: 50px;
	background-color: $background-color_3;
	padding: 30px 0;
	width: 100%;
	box-shadow: 0 -5px 20px rgba(0, 0, 0, 0.1);
	animation: slideUp 1s forwards;
	animation-delay: 0.8s;
	opacity: 0;
	transform: translateY(50px);
	p {
		font-size: 18px;
		color: $color_3;
		margin-bottom: 20px;
	}
}
.trusted-content {
	max-width: 1200px;
	margin: 0 auto;
	text-align: center;
	padding: 0 15px;
}
#count {
	font-weight: bold;
	color: $color_4;
}
.logo-carousel {
	display: flex;
	justify-content: center;
	flex-wrap: wrap;
	gap: 40px;
	img {
		height: 40px;
		width: auto;
		opacity: 0.8;
		transition: opacity 0.3s ease;
		&:hover {
			opacity: 1;
		}
	}
}
.animated.bounce.active {
	animation: bounce 2s ease infinite;
}
.ux-shape-divider {
	width: 100%;
	height: 150px;
}
@media (max-width: 992px) {
	.container {
		flex-direction: column;
	}
	.hero-content {
		padding-right: 0;
		margin-bottom: 40px;
		text-align: center;
	}
	.icon-list {
		li {
			text-align: left;
		}
	}
	.hero-image-container {
		width: 100%;
		max-width: 500px;
	}
	.trusted-by {
		margin-top: 30px;
	}
}
@media (max-width: 768px) {
	.simplepage-hero {
		padding: 40px 0 0;
	}
	.heading-title {
		font-size: 36px;
	}
	.subtitle {
		font-size: 24px;
	}
	.logo-carousel {
		gap: 20px;
		img {
			height: 30px;
		}
	}
}
@media (max-width: 576px) {
	.heading-title {
		font-size: 28px;
	}
	.subtitle {
		font-size: 20px;
	}
	.btn-primary {
		padding: 12px 25px;
		font-size: 16px;
	}
	.circle-element {
		display: none;
	}
}
</style>
