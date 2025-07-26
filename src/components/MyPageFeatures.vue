<template>
	<div class="background" ref="backgroundRef">
		<div class="container">
			<div class="main-content">
				<div class="heading-section">
					<div class="mark">
						<h2 class="heading-text">SIÊU ƯU ĐÃI</h2>
					</div>
					<h2 class="heading-text-2">
						khi thiết kế website tại MYPAGE
					</h2>
				</div>
				<div class="paragraph-section">
					<p class="paragraph-text">
						Khi sử dụng
						<span class="strong-text">dịch vụ thiết kế web</span>
						tại <span class="strong-text">MYPAGE</span>, quý khách
						được các quà tặng sau:
					</p>
				</div>
				<div class="features-container">
					<div class="feature-item">
						<div class="feature-icon-wrapper">
							<div class="feature-icon-bg">
								<div class="icon-container">
									<!-- Icon for TÊN MIỀN - Placeholder for SVG -->
									<img
										src="/images/services/domain.svg"
										alt="Domain Icon"
										width="42"
										height="42"
									/>
								</div>
							</div>
						</div>
						<div class="feature-content">
							<h3 class="feature-heading">TÊN MIỀN</h3>
							<p class="feature-description">
								Tặng ngay chi phí đăng ký tên miền
								.com/.net/.vn/.com.vn năm đầu tiên
							</p>
						</div>
					</div>
					<div class="feature-item">
						<div class="feature-icon-wrapper">
							<div class="feature-icon-bg">
								<div class="icon-container">
									<!-- Icon for HOSTING - Placeholder for SVG -->
									<img
										src="/images/services/hosting.svg"
										alt="Hosting Icon"
										width="42"
										height="42"
									/>
								</div>
							</div>
						</div>
						<div class="feature-content">
							<h3 class="feature-heading">HOSTING</h3>
							<p class="feature-description">
								Tặng ngay hosting chất lượng cao, băng thông
								không giới hạn
							</p>
						</div>
					</div>
					<div class="feature-item">
						<div class="feature-icon-wrapper">
							<div class="feature-icon-bg">
								<div class="icon-container">
									<!-- Icon for EMAIL - Placeholder for SVG -->
									<img
										src="/images/services/mail.svg"
										alt="Email Icon"
										width="42"
										height="42"
									/>
								</div>
							</div>
						</div>
						<div class="feature-content">
							<h3 class="feature-heading">EMAIL</h3>
							<p class="feature-description">
								Tặng ngay 5 email doanh nghiệp (email theo tên
								miền của bạn)
							</p>
						</div>
					</div>
				</div>
				<div class="buttons-container">
					<button class="button primary-button">
						<span></span>
						<span></span>
						<span></span>
						<span></span>
						<strong class="button-text">ĐĂNG KÝ</strong>
					</button>
					<button class="button secondary-button">
						<span></span>
						<span></span>
						<span></span>
						<span></span>
						<strong class="button-text">BẢNG GIÁ</strong>
					</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const backgroundRef = ref<HTMLElement | null>(null);
const minWidth = 992; // px
const maxWidth = 100; // %

const handleScroll = () => {
    if (!backgroundRef.value) return;

    const element = backgroundRef.value;
    const rect = element.getBoundingClientRect();
    const viewportHeight = window.innerHeight;

    // Calculate the center of the component relative to the viewport
    const elementCenter = rect.top + rect.height / 2;
    const viewportCenter = viewportHeight / 2;

    // Distance from the component's center to the viewport's center
    const distance = Math.abs(elementCenter - viewportCenter);

    // Define the scroll zone where the width changes
    // This zone starts when the component is fully visible and ends when it's fully out
    // Or, more precisely, when its center is within a certain range of the viewport center
    const scrollZone = viewportHeight / 2 + rect.height / 2; // Distance from center to edge of scroll effect

    let currentWidth: number;
	let unit = 'px'; // Default unit is px

	if (elementCenter - viewportCenter < 0) {
		// Component is above the active scroll zone
		currentWidth = maxWidth;
		unit = '%';
	}
    else if (distance >= scrollZone) {
        // Component is far below the active scroll zone
        currentWidth = minWidth;
	} else {
        // Component is within the scroll zone, calculate interpolated width
        // Progress from 0 (at edge of scroll zone) to 1 (at viewport center)
        const progress = 1 - (distance / scrollZone);
        
        // Interpolate width from minWidth to maxWidth
        // We want to go from 992px to 100%
        // Let's assume 100% is equivalent to a very large pixel value for calculation,
        // or we can directly set the style property as a percentage.
        // For simplicity, let's calculate a percentage value.
        // The width will be a mix of minWidth (px) and maxWidth (%)
        // This requires setting a CSS variable.

        // Calculate a value between 0 and 1, where 0 is minWidth and 1 is maxWidth
        // We'll use a linear interpolation for the percentage part
        const interpolatedPercentage = progress * (maxWidth - (minWidth / window.innerWidth * 100)); // Adjust minWidth to % for interpolation
        currentWidth = Math.max(minWidth, (window.innerWidth * interpolatedPercentage / 100)); // This is tricky with mixed units.

        // Let's simplify: we want to transition from 992px to 100vw.
        // We'll use a CSS custom property for the width.
        // The value will be a percentage, but we need to ensure it doesn't go below 992px.
        const targetWidthPx = window.innerWidth; // 100% of viewport width
        const widthRange = targetWidthPx - minWidth;
        const calculatedWidthPx = minWidth + (widthRange * progress);
        
        currentWidth = Math.min(targetWidthPx, Math.max(minWidth, calculatedWidthPx));
    }
    
    // Apply the calculated width
	element.style.width = `${currentWidth}${unit}`;
    element.style.maxWidth = '100%'; // Ensure it doesn't exceed 100% of parent
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    // Initial call to set the correct width on load
    handleScroll();
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped lang="scss">
.background {
	padding: 60px 40px;
	// min-width: 992px; // Removed, controlled by JS
	// width: 992px; // Removed, controlled by JS
	// max-width: 100%; // Removed, controlled by JS
	display: flex;
	flex-direction: column;
	text-align: center;
	color: #fff;
	background-image: linear-gradient(
		to right,
		#626262 0,
		#000000 50%,
		#626262 100%
	);
	background-color: #626262;
	position: relative;
	overflow: hidden;
	margin: auto;

	&::before,
	&::after {
		content: "";
		position: absolute;
		top: 0;
		height: 100%;
		background-image: url("/images/services/dot-left.png");
		background-repeat: no-repeat;
		background-size: cover;
		z-index: 1;
		width: 30%;
		opacity: 0.2;
		display: block;
	}

	&::before {
		left: 0;
		background-position: left center;
	}

	&::after {
		right: 0;
		background-position: right center;
		transform: scale(-1, 1);
		filter: brightness(0) invert(1);
		opacity: 0.1;
	}
}

.container {
	display: flex;
	flex-direction: row;
	justify-content: stretch;
	align-items: stretch;
	flex-wrap: wrap;
	width: 100%;
}

.main-content {
	padding: 0 15px;
	width: 100%;
	display: flex;
	flex-direction: column;
	align-items: center; /* Center content horizontally */
	gap: 30px;
	z-index: 2;
}

.heading-section {
	display: flex;
	flex-direction: row;
	justify-content: center;
	gap: 0; /* Figma shows -2.842170943040401e-14px, so effectively 0 */
}

.mark {
	display: flex;
	flex-direction: row;
	justify-content: center;
	padding: 0 10px;
	position: relative;
}

.heading-text {
	font-family: "Inter", sans-serif;
	font-weight: 700;
	font-size: 30px;
	line-height: 1.21em;
	text-align: center;
	color: #ffffff;
	position: relative; /* To place text above gradient */
	z-index: 1;
	padding: 0 10px;

	&::before {
		    position: absolute;
    left: 0;
    z-index: -1;
    bottom: 0;
	    content: "";
    height: 100%;
    width: 0%;
    background-color: #08c;
	background: linear-gradient(90deg , rgba(11,255,0,0.06) 0%, rgba(11,255,0,0.33) 100%);
	animation: highlightProgress 1s both;
	}

	@keyframes highlightProgress {
		from {
			width: 0%;
		}
		to {
			width: 100%;
		}
	}
}

.heading-text-2 {
	font-family: "Inter", sans-serif;
	font-weight: 700;
	font-size: 29px;
	line-height: 1.21em;
	text-align: center;
	color: #ffffff;
}

.paragraph-section {
	display: flex;
	flex-direction: row;
	justify-content: center;
}

.paragraph-text {
	font-family: "Inter", sans-serif;
	font-weight: 400;
	font-size: 18.4375px;
	line-height: 1.41em;
	text-align: center;
	color: #ffffff;
}

.strong-text {
	font-weight: 700;
}

.features-container {
	display: flex;
	flex-direction: row;
	justify-content: stretch;
	align-items: stretch;
	flex-wrap: wrap;
}

.feature-item {
	display: flex;
	flex-direction: column;
	align-items: center;
	padding: 30px 15px 20px;
	flex: 1; /* Distribute space evenly */
}

.feature-icon-wrapper {
	display: flex;
	flex-direction: column;
	align-items: center;
	padding: 0 0 15px;
	width: 100%;
}

.feature-icon-bg {
	display: flex;
	flex-direction: row;
	justify-content: center;
	padding: 30px;
	border-radius: 51px;
	background: linear-gradient(
		to right,
		rgba(48, 49, 255, 0.64),
		rgba(118, 255, 201, 0.53)
	);
	box-shadow: 0px 0px 32px -7px rgba(255, 255, 255, 0.5);
}

.icon-container {
	display: flex;
	flex-direction: row;
}

.feature-content {
	display: flex;
	flex-direction: column;
	align-items: center;
	width: 100%;
	gap: 15.01px;
}

.feature-heading {
	font-family: "Inter", sans-serif;
	font-weight: 700;
	font-size: 24px;
	line-height: 1.25em;
	text-align: center;
	color: #ffffff;
}

.feature-description {
	font-family: "Inter", sans-serif;
	font-weight: 400;
	font-size: 18px;
	line-height: 1.43em;
	text-align: center;
	color: #ffffff;
}

.buttons-container {
	display: flex;
	flex-direction: row;
	justify-content: center;
	gap: 20px; /* Add some space between buttons */
}

.button {
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
	padding: 15px 45px;
	border: none;
	cursor: pointer;
	position: relative;
	background: linear-gradient(90deg,#008acd, #23c1e5) 50%,#008acd;
	box-shadow: inset 0 0 10px rgb(2 125 232 / 61%), 0 0 9px 3px rgb(1 111 164 / 50%);
	overflow: hidden;
	transition: box-shadow 0.3s;

	&::before {
		content: "";
		position: absolute;
		left: -4em;
		width: 4em;
		height: 100%;
		top: 0;
		transition: transform .4s ease-in-out;
		background: linear-gradient(to right, transparent 1%, rgba(27, 253, 156, 0.3) 40%,rgba(27, 253, 156, 0.3) 60% , transparent 100%);		
	}

	&:hover {
		box-shadow: rgba(27, 253, 156, 0.6) 0px 0px 10px 0px inset, rgba(27, 252, 156, 0.2) 0px 0px 9px 3px;

		&::before {
			transform: translateX(15em);
		}
	}

	$line-color: #93fffe;
	$transparent-color: rgba(43, 8, 8, 0);
	$animation-duration: 2s;

	@mixin border-line($top, $right, $bottom, $left, $width, $height, $gradient-direction, $animation-name, $animation-delay: 0s) {
		top: $top;
		right: $right;
		bottom: $bottom;
		left: $left;
		width: $width;
		height: $height;
		background: linear-gradient($gradient-direction, $transparent-color, $line-color);
		animation: $animation-duration $animation-name linear $animation-delay infinite;
	}

	span {
		position: absolute;

		&:nth-child(1) {
			@include border-line(0, null, null, 0, 100%, 2px, to left, animateTop);
		}

		&:nth-child(2) {
			@include border-line(0, 0, null, null, 2px, 100%, to top, animateRight, -1s);
		}

		&:nth-child(3) {
			@include border-line(null, null, 0, 0, 100%, 2px, to right, animateBottom);
		}

		&:nth-child(4) {
			@include border-line(0, null, null, 0, 2px, 100%, to bottom, animateLeft, -1s);
		}

		@keyframes animateLeft {
			0% { transform: translateY(-100%); }
			100% { transform: translateY(100%); }
		}

		@keyframes animateRight {
			0% { transform: translateY(100%); }
			100% { transform: translateY(-100%); }
		}

		@keyframes animateBottom {
			0% { transform: translateX(-100%); }
			100% { transform: translateX(100%); }
		}

		@keyframes animateTop {
			0% { transform: translateX(100%); }
			100% { transform: translateX(-100%); }
		}
	}
}

.button-text {
	font-family: "Inter", sans-serif;
	font-weight: 700;
	font-size: 16px;
	line-height: 1.61em;
	letter-spacing: 6.22%;
	text-align: center;
	color: #ffffff;
}
</style>
