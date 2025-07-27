<template>
  <section class="ngon-share-section">
    <div class="container">
      <div class="content-wrapper">
        <div class="heading-container">
          <h2 class="heading">NGON SHARE - “CHO LÀ NHẬN”</h2>
        </div>
        <div class="text-container">
          <p class="description">
            Không chỉ tiên phong trong việc nghiên cứu và ứng dụng những kiến thức mới về Google Marketing nói riêng và Digital Marketing nói chung, SEONGON còn luôn chăm chỉ chia sẻ “những gì mình biết và những gì mình làm” đến với cộng đồng
          </p>
        </div>
        <div class="image-grid">
          <div class="grid-item grid-item-1">
            <img src="/images/ngonshare/Frame-58-56586a.png" alt="Image 1" class="grid-image" />
            <div class="overlay-text">
              <p>10 năm thực thi các chiến dịch Google Marketing</p>
            </div>
          </div>
          <div class="grid-item grid-item-2">
            <img src="/images/ngonshare/Frame-61-56586a.png" alt="Image 2" class="grid-image" />
            <div class="overlay-text">
              <p>200+ workshop khóa học sự kiện</p>
            </div>
          </div>
          <div class="grid-item grid-item-3">
            <img src="/images/ngonshare/Frame-59-56586a.png" alt="Image 3" class="grid-image" />
          </div>
          <div class="grid-item grid-item-4">
            <img src="/images/ngonshare/sec-8-anh-2-56586a.png" alt="Image 4" class="grid-image" />
          </div>
          <div class="grid-item grid-item-5">
            <img src="/images/ngonshare/sec-8-anh-3-56586a.png" alt="Image 5" class="grid-image" />
          </div>
          <div class="grid-item grid-item-6">
            <img src="/images/ngonshare/sec-8-anh-1-56586a.png" alt="Image 6" class="grid-image" />
            <div class="overlay-text">
              <p>650+ bài chia sẻ chuyên môn</p>
            </div>
          </div>
          <div class="grid-item grid-item-7">
            <img src="/images/ngonshare/Frame-64-56586a.png" alt="Image 7" class="grid-image" />
            <div class="overlay-text">
              <p>50+ case study về dự án</p>
            </div>
          </div>
          <div class="grid-item grid-item-8">
            <img src="/images/ngonshare/sec-8-anh-1-56586a.png" alt="Image 8" class="grid-image" />
          </div>
          <div class="grid-item grid-item-9">
            <img src="/images/ngonshare/sec-8-anh-1-56586a.png" alt="Image 8" class="grid-image" />
          </div>
          <div class="grid-item grid-item-10">
            <img src="/images/ngonshare/sec-8-anh-1-56586a.png" alt="Image 8" class="grid-image" />
          </div>
          <div class="grid-item grid-item-11">
            <img src="/images/ngonshare/sec-8-anh-1-56586a.png" alt="Image 8" class="grid-image" />
          </div>
          <div class="grid-item grid-item-12">
            <img src="/images/ngonshare/sec-8-anh-1-56586a.png" alt="Image 8" class="grid-image" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted, onUnmounted, ref } from 'vue';

export default defineComponent({
  name: 'NgonShareSection',
  setup() {
    const gridItems = ref<HTMLElement[]>([]);
    let observer: IntersectionObserver | null = null;

    onMounted(() => {
      gridItems.value = Array.from(document.querySelectorAll('.grid-item'));

      observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              observer?.unobserve(entry.target); // Optional: uncomment to run animation only once
            } else {
              entry.target.classList.remove('is-visible'); // Optional: uncomment to reset animation when out of view
            }
          });
        },
        { threshold: 0.1 } // Trigger when 10% of the item is visible
      );

      gridItems.value.forEach((item) => {
        observer?.observe(item);
      });
    });

    onUnmounted(() => {
      observer?.disconnect();
    });

    return {
      gridItems,
    };
  },
});
</script>

<style lang="scss" scoped>
.ngon-share-section {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 1216px;
  background-color: #F8FDFF;

  .container {
    display: flex;
    flex-direction: row;
    justify-content: stretch;
    align-items: stretch;
    align-self: stretch;
    width: 100%;
    height: auto;
  }

  .content-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    align-self: stretch;
    width: 100%;
    height: 100%;
  }

  .heading-container {
    display: flex;
    flex-direction: column;
    align-self: stretch;
    height: 80px;
  }

  .heading {
    display: flex;
    flex-direction: column;
    align-items: center;
    align-self: stretch;
    font-family: 'Inter';
    font-weight: 700;
    font-size: 30.25px;
    line-height: 1.322314049586777em;
    letter-spacing: 2.644628138581583%;
    text-align: center;
    color: #000000;
  }

  .text-container {
    padding: 5px 0px 39.38999938964844px;
    width: 950px;
    height: 92.39px;
  }

  .description {
    font-family: 'Inter';
    font-weight: 400;
    font-size: 15.375px;
    line-height: 1.5609756097560976em;
    text-align: center;
    color: #000000;
  }

  .image-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr); /* 4 columns */
    grid-template-rows: repeat(3, auto); /* 3 rows, auto height */
    gap: 8px; /* Gap between grid items */
    width: 100%; /* Fixed width as per Figma */
    margin-top: 39px; /* Spacing from text-container */
    position: relative; /* For absolute positioning of dots */
  }

  .grid-item {
    position: relative;
    overflow: hidden;
    border-radius: 8px; /* Apply border-radius from Figma */
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.8s ease-out, transform 0.8s ease-out;

    @for $i from 1 through 12 {
      &.grid-item-#{$i} {
        transition-delay: #{$i * 0.2}s;
      }
    }

    &.is-visible {
      opacity: 1;
      transform: translateY(0);
    }

    .grid-image {
      width: 100%;
      height: 100%;
      object-fit: cover; /* Cover the area */
      display: block;
    }

    .overlay-text {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      background: linear-gradient(to top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0));
      color: #ffffff;
      padding: 10px;
      box-sizing: border-box;
      font-family: 'Inter';
      font-weight: 700;
      font-size: 20px;
      line-height: 1.2;
      text-align: left;
      display: flex;
      align-items: flex-end;
      height: 100%; /* Take full height to align text at bottom */
      p {
        margin: 0;
        padding-bottom: 10px; /* Padding for text inside overlay */
      }
    }

    .view-more {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: #000000; /* Black background for "Xem thêm" */
      opacity: 0.8; /* Opacity as per Figma */
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: #ffffff;
      font-family: 'Inter';
      font-weight: 600;
      font-size: 18px;
      cursor: pointer;

      img {
        width: 24px;
        height: 24px;
        margin-top: 8px;
      }
    }
  }

  /* Specific grid item sizing and positioning */
  .grid-item-1 {
    grid-column: 1 / span 2; /* Spans 2 columns */
    grid-row: 1 / span 2; /* Spans 2 rows */
    height: 400px; /* Fixed height */
  }

  .grid-item-2 {
    grid-column: 3 / span 2; /* Spans 2 columns */
    grid-row: 1 / span 1; /* Spans 1 row */
    height: 196px; /* Fixed height */
  }

  .grid-item-3 {
    grid-column: 3 / span 1; /* Spans 1 column */
    grid-row: 2 / span 1; /* Spans 1 row */
    height: 196px; /* Fixed height */
  }

  .grid-item-4 {
    grid-column: 5 / span 2; /* Spans 1 column */
    grid-row: 1 / span 1; /* Spans 1 row */
    height: 196px; /* Fixed height */
  }

  .grid-item-5 {
    grid-column: 3 / span 1; /* Spans 1 column */
    grid-row: 3 / span 1; /* Spans 1 row */
    // height: 208px; /* Fixed height */
    height: 196px;
  }

  .grid-item-6 {
    grid-column: 4 / span 1; /* Spans 1 column */
    grid-row: 2 / span 2; /* Spans 2 rows */
    height: 400px; /* Fixed height */
  }

  .grid-item-7 {
    grid-column: 1 / span 2; /* Spans 2 columns */
    grid-row: 3 / span 1; /* Spans 1 row */
    // height: 208px; /* Fixed height */
    height: 196px;
  }

  .grid-item-8 {
    grid-column: 5 / span 2; /* Spans 1 column */
    grid-row: 2 / span 1; /* This item is not explicitly in the Figma, but based on the image, it seems to be a placeholder or part of a larger image. I'll remove it for now as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
    height: 196px; /* Fixed height */
  }

  .grid-item-9 {
    grid-column: 1 / span 1; /* Spans 1 column */
    grid-row: 4 / span 1; /* This item is not explicitly in the Figma, but based on the image, it seems to be a placeholder or part of a larger image. I'll remove it for now as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
    height: 196px; /* Hide this item as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
  }

  .grid-item-10 {
    grid-column: 2 / span 1; /* Spans 1 column */
    grid-row: 4 / span 1; /* This item is not explicitly in the Figma, but based on the image, it seems to be a placeholder or part of a larger image. I'll remove it for now as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
    height: 196px; /* Hide this item as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
  }

  .grid-item-11 {
    grid-column: 3 / span 2; /* Spans 1 column */
    grid-row: 4 / span 1; /* This item is not explicitly in the Figma, but based on the image, it seems to be a placeholder or part of a larger image. I'll remove it for now as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
    height: 196px; /* Hide this item as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
  }

  .grid-item-12 {
    grid-column: 5 / span 2; /* Spans 1 column */
    grid-row: 3 / span 2; /* This item is not explicitly in the Figma, but based on the image, it seems to be a placeholder or part of a larger image. I'll remove it for now as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
    height: 400px; /* Hide this item as it's not clearly defined in the Figma data as a separate image with specific dimensions. */
  }
}
</style>