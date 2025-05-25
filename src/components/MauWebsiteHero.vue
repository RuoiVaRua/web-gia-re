<template>
	<section class="mauwebsite-hero">
		<div class="hero-background">
			<div class="background-gradient"></div>
			<div class="background-shapes">
				<div class="web-collage"></div>
			</div>
		</div>
		<div class="container">
			<div class="hero-content">
				<h1 class="title animated fadeIn">
					MÃ NGUỒN BẠN SỞ HỮU RIÊNG KHÔNG PHỤ THUỘC, KHÔNG CHUNG ĐỤNG
				</h1>
				<div class="pricing animated fadeIn">
					<span class="pricing-text">Giá không thấp nhưng</span>
					<span class="pricing-highlight">sở hữu riêng mã nguồn</span>
				</div>
				<ul class="feature-list animated fadeIn">
					<li>
						Chất lượng sản phẩm đầu cuối thật sự chất lượng ( xem
						ngay các dự án đã làm cho khách hàng của chúng tôi )
					</li>
					<li>
						Chi phí thấp nhất để có một website đẹp lung linh nhất
					</li>
					<li>
						Bạn không cần phải thiết kế riêng nếu không thật sự có
						nhu cầu đó
					</li>
					<li>
						Bạn trót yêu một trong những mẫu website đẹp của chúng
						tôi
					</li>
				</ul>
			</div>
		</div>
		<div class="website-showcase-wrapper">
			<div class="website-showcase animated fadeIn">
				<!-- Website mockups arranged in layers -->
				<div class="website-preview" style="left: 50%; top: 0px">
					<img
						src="https://mauwebsite.vn/wp-content/uploads/2018/11/1.png"
						alt="Website Design"
					/>
				</div>
				<div class="website-preview" style="left: -30px; top: 30px">
					<img
						src="https://mauwebsite.vn/wp-content/uploads/2018/11/2.png"
						alt="Website Design"
					/>
				</div>

				<!-- Center MacBook with main website preview -->
				<div
					class="website-preview"
					style="
						top: 120px;
						left: 50%;
						transform: translateX(-50%);
						width: 480px;
						max-width: 100%;
					"
				>
					<img
						src="https://mauwebsite.vn/wp-content/uploads/2018/11/3.png"
						alt="Main Website Design"
					/>
				</div>

				<!-- Right side website previews -->
				<div class="website-preview" style="right: -50px; top: 10px">
					<img
						src="https://mauwebsite.vn/wp-content/uploads/2018/11/4.png"
						alt="Website Design"
					/>
				</div>
				<div
					class="website-preview"
					style="left: 50%; top: 40px; margin-left: 110px"
				>
					<img
						src="https://mauwebsite.vn/wp-content/uploads/2018/11/5.png"
						alt="Mobile App"
					/>
				</div>
				<div
					class="website-preview"
					style="top: 220px; left: -40px"
				>
					<img
						src="https://mauwebsite.vn/wp-content/uploads/2018/11/6.png"
						alt="Website Design"
					/>
				</div>
			</div>
		</div>
	</section>
</template>

<script lang="ts">
export default {
	name: "MauWebsiteHero",
	mounted() {
		// Add animation classes after component mounts
		setTimeout(() => {
			const animatedElements = document.querySelectorAll(".animated");
			animatedElements.forEach((el, index) => {
				setTimeout(() => {
					el.classList.add("active");
				}, index * 150);
			});
		}, 300);

		// Hiệu ứng xuất hiện lần lượt cho website-preview
		const previews = document.querySelectorAll<HTMLElement>(".website-preview");
		previews.forEach((el, idx) => {
			setTimeout(() => {
				el.classList.add("active");
			}, 600 + idx * 70);
		});

		// Add mousemove effect to website previews
		const previewImages = document.querySelectorAll(".website-preview img");
		previewImages.forEach((img) => {
			img.addEventListener("mousemove", this.handleImgMouseMove as EventListener);
			img.addEventListener("mouseleave", this.handleImgMouseLeave as EventListener);
		});
	},
	methods: {
		handleImgMouseMove: (e: MouseEvent) => {
			if (!e.target) return;
			/** @type {HTMLImageElement} */
			const imageElement = e.target as HTMLImageElement;
			const { offsetX, offsetY } = e;
			const { offsetWidth, offsetHeight } = imageElement;

			// Calculate position relative to the center of the image
			const centerX = offsetWidth / 2;
			const centerY = offsetHeight / 2;

			// Calculate movement based on mouse position relative to center
			// Move inverse to mouse direction
			const moveX = ((offsetX - centerX) / centerX) * -10; // Adjust sensitivity (10px max movement)
			const moveY = ((offsetY - centerY) / centerY) * -10; // Adjust sensitivity (10px max movement)

			// Zoom factor (e.g., 1.1 for 10% zoom)
			const zoom = 1.05;

			// Apply transform using matrix(scaleX, skewY, skewX, scaleY, translateX, translateY)
			// For simple zoom and translation, skew values are 0.
			// matrix(scaleX, 0, 0, scaleY, translateX, translateY)
			imageElement.style.transform = `matrix(${zoom}, 0, 0, ${zoom}, ${moveX}, ${moveY})`;
		},
		handleImgMouseLeave: (e: MouseEvent) => {
			// Reset transform on mouse leave
			/** @type {HTMLImageElement} */
			const imageElement = e.target as HTMLImageElement;
			imageElement.style.transform = "matrix(1, 0, 0, 1, 0, 0)"; // Reset to original scale and position
		}
	}
};
</script>

<style scoped lang="scss">
$color_1: #fff;
$color_2: #ff3d71;
$font-family_1: "Roboto", sans-serif;

/* Website showcase section */
/* Macbook container */
/* Website previews */
/* Left side previews */
/* Right side previews */
/* Phone mockup */
/* Preview types */
/* Animations */
/* Responsive adjustments */
.mauwebsite-hero {
	position: relative;
	min-height: 100vh;
	padding: 60px 0 0;
	font-family: $font-family_1;
	overflow: hidden;
	color: $color_1;
}
.hero-background {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	z-index: -1;
}
.background-gradient {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: linear-gradient(135deg, #1e0644 0%, #2a0a50 100%);
	opacity: 0.95;
}
.web-collage {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-image: url("https://mauwebsite.vn/wp-content/themes/flatsome-child/assets/images/bg-collage.jpg");
	background-size: cover;
	background-position: center;
	opacity: 0.15;
}
.container {
	max-width: 1200px;
	margin: 0 auto;
	padding: 0 20px;
	position: relative;
	z-index: 2;
}
.hero-content {
	max-width: 700px;
	margin: 0 auto 70px;
}
.title {
	font-size: 36px;
	color: $color_1;
	margin-bottom: 20px;
	font-weight: 700;
	line-height: 1.3;
	text-transform: uppercase;
	text-align: center;
}
.pricing {
	margin-bottom: 30px;
	display: flex;
	align-items: center;
	justify-content: center;
	font-size: 28px;
	font-weight: 600;
}
.pricing-text {
	margin-right: 15px;
}
.pricing-highlight {
	color: $color_2;
}
.feature-list {
	list-style: none;
	padding: 0;
	margin: 0 auto;
	max-width: 600px;
	li {
		position: relative;
		padding-left: 20px;
		margin-bottom: 15px;
		font-size: 16px;
		line-height: 1.5;
		&::before {
			content: "•";
			position: absolute;
			left: 0;
			color: $color_2;
			font-size: 18px;
		}
	}
}
.website-showcase-wrapper {
	position: relative;
	height: 650px;
	width: 100%;
	margin: 0 auto;
}
.website-showcase {
	position: relative;
	width: 100%;
	max-width: 960px;
	height: 100%;
	max-height: 300px;
	margin: 0 auto;
	perspective: 1000px;
}
.macbook-container {
	position: absolute;
	top: 30%;
	left: 50%;
	transform: translate(-50%, -20%);
	width: 800px;
	z-index: 3;
}
.macbook {
	position: relative;
	width: 100%;
	padding-bottom: 52%;
	background-image: url("https://mauwebsite.vn/wp-content/themes/flatsome-child/assets/images/macbook.png");
	background-size: contain;
	background-position: center;
	background-repeat: no-repeat;
}
.macbook-screen {
	position: absolute;
	top: 5.8%;
	left: 11.7%;
	width: 76.6%;
	height: 80.5%;
	overflow: hidden;
	border-radius: 3px;
	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
}
.website-preview {
	position: absolute;
	border-radius: 6px;
	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		display: block;
		transition: transform 0.3s ease-out; /* Thêm transition cho hiệu ứng mượt mà */
		transform-origin: center center; /* Đặt gốc transform ở giữa ảnh */
	}
	opacity: 0.1;
	margin-top: 300px;
	transition: opacity 0.7s cubic-bezier(0.4,0,0.2,1), margin-top 0.7s cubic-bezier(0.4,0,0.2,1);
}
.website-preview.active {
	opacity: 1;
	margin-top: 0;
}
.left-top {
	top: 10%;
	left: 3%;
	width: 350px;
	height: 250px;
	z-index: 2;
	transform: rotate(-8deg);
}
.left-bottom {
	bottom: 10%;
	left: 6%;
	width: 390px;
	height: 260px;
	z-index: 1;
	transform: rotate(5deg);
}
.right-top {
	top: 0;
	right: 3%;
	width: 350px;
	height: 240px;
	z-index: 2;
	transform: rotate(6deg);
	position: relative;
}
.right-bottom {
	bottom: 5%;
	right: 5%;
	width: 420px;
	height: 270px;
	z-index: 1;
	transform: rotate(-4deg);
}
.phone-mockup {
	position: absolute;
	bottom: -40px;
	right: -50px;
	width: 140px;
	height: 280px;
	z-index: 4;
	border-radius: 20px;
	overflow: hidden;
	box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
}
.preview-dark {
	box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
}
.preview-interior {
	box-shadow: 0 10px 25px rgba(0, 0, 0, 0.35);
}
.preview-phone {
	box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
}
.preview-light {
	box-shadow: 0 10px 25px rgba(0, 0, 0, 0.25);
}
.animated {
	opacity: 0;
	transition: all 0.8s ease;
}
.fadeIn {
	transform: translateY(20px);
}
.fadeIn.active {
	opacity: 1;
	transform: translateY(0);
}
@media (max-width: 1300px) {
	.macbook-container {
		width: 650px;
	}
	.left-top {
		width: 300px;
		height: 200px;
	}
	.right-top {
		width: 300px;
		height: 200px;
	}
	.left-bottom {
		width: 330px;
		height: 210px;
	}
	.right-bottom {
		width: 330px;
		height: 210px;
	}
	.phone-mockup {
		width: 120px;
		height: 240px;
	}
}
@media (max-width: 992px) {
	.title {
		font-size: 32px;
	}
	.pricing {
		font-size: 24px;
		flex-direction: column;
		align-items: center;
	}
	.pricing-text {
		margin-right: 0;
		margin-bottom: 5px;
	}
	.website-showcase-wrapper {
		height: 500px;
	}
	.macbook-container {
		width: 500px;
	}
	.left-top {
		width: 240px;
		height: 160px;
	}
	.right-top {
		width: 240px;
		height: 160px;
	}
	.left-bottom {
		width: 260px;
		height: 170px;
	}
	.right-bottom {
		width: 260px;
		height: 170px;
	}
	.phone-mockup {
		width: 100px;
		height: 200px;
		right: -30px;
		bottom: -30px;
	}
}
@media (max-width: 768px) {
	.mauwebsite-hero {
		padding: 40px 0;
	}
	.title {
		font-size: 26px;
	}
	.website-showcase-wrapper {
		height: 450px;
	}
	.macbook-container {
		width: 400px;
	}
	.left-top {
		left: 0;
		top: 5%;
	}
	.right-top {
		right: 0;
		top: 5%;
	}
	.left-bottom {
		left: 0;
		bottom: 10%;
	}
	.right-bottom {
		right: 0;
		bottom: 10%;
	}
	.phone-mockup {
		width: 80px;
		height: 160px;
	}
}
@media (max-width: 576px) {
	.title {
		font-size: 22px;
	}
	.website-showcase-wrapper {
		height: 400px;
	}
	.macbook-container {
		width: 300px;
	}
	.left-top {
		width: 180px;
		height: 120px;
	}
	.right-top {
		width: 180px;
		height: 120px;
	}
	.left-bottom {
		width: 180px;
		height: 120px;
	}
	.right-bottom {
		width: 180px;
		height: 120px;
	}
	.phone-mockup {
		width: 60px;
		height: 120px;
		right: -20px;
		bottom: -20px;
	}
}
</style>
