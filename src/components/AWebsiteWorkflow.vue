<template>
  <section class="figma-process-section">
    <div class="figma-container">
      <div class="figma-header-section">
        <div class="figma-header-left">
          <h4 class="figma-header-title">Quy trình thực hiện</h4>
          <p class="figma-header-description">
            Quy trình thiết kế Website chuyên nghiệp, chuẩn UX/UI, lập trình theo
            tiêu chuẩn mới nhất hiện nay và thiết kế không trùng lắp các mẫu nào
            trên thị trường, sự khác biệt tạo nên đẳng cấp và chuyên nghiệp cho
            Website của bạn
          </p>
        </div>
        <div class="figma-header-right">
          <span class="figma-design-text">Website Design</span>
          <div class="figma-buttons-wrapper">
            <button class="figma-button-prev">
              <img src="/images/icons/arrow_left.svg" alt="Previous" />
            </button>
            <button class="figma-button-next">
              <img src="/images/icons/arrow_right.svg" alt="Next" />
            </button>
          </div>
        </div>
      </div>
      <div class="figma-process-list">
        <div v-for="(step, index) in processSteps" :key="index" class="figma-process-item">
          <div class="figma-process-item__content">
            <div class="figma-process-item__image">
              <img :src="step.image" :alt="step.title" />
              <div class="figma-process-item__gradient"></div>
            </div>            
            <div class="figma-process-item__info">
              <div class="figma-process-item__title">{{ step.title }}</div>
              <div class="figma-process-item__number">{{ step.number }}</div>
              <!-- <div class="figma-process-item__line"></div> -->
            </div>            
            <p class="figma-process-item__description">{{ step.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'FigmaProcessSection',
  setup() {
    const processSteps = [
      {
        title: 'Thu thập ý tưởng',
        description: 'Thu thập ý tưởng của khách hàng, cùng trao đổi, thảo luận thống nhất các ý tưởng để hình thành sơ bộ câu chuyện của website. Hành trình thiết kế ra một website hoàn hảo thì ý tưởng chính là phần quan trọng nhất.',
        number: '1',
        image: '/images/process/step1-55cfd8.png'
      },
      {
        title: 'Thiết kế UX/UI',
        description: 'A Website sẽ giúp khách hàng thiết kế giao diện UX/UI, thể hiện câu chuyện mong muốn trên website. Mỗi một giao diện đều có ý nghĩa to lớn trong việc kinh doanh của quý khách.',
        number: '2',
        image: '/images/process/step2-55cfd8.png'
      },
      {
        title: 'Lập trình chuẩn SEO',
        description: 'Với đội ngũ IT hơn 10 năm kinh nghiệm, từ giao diện đến hệ thống được A Website tối ưu, giúp website của bạn chuẩn SEO và thân thiện các máy chủ tìm kiếm. Từ đó tiếp cận được các khách hàng tiềm năng dễ dàng',
        number: '3',
        image: '/images/process/step3-55cfd8.png'
      },
      {
        title: 'Bàn giao Website',
        description: 'Sau khi nhận trang Website, việc đầu tiên là sử dụng và cập nhật các thông tin lên trang website. Đừng lo, chúng tôi sẽ hướng dẫn bạn cách sử dụng và chăm sóc cho website như thế nào là tốt nhất.',
        number: '4',
        image: '/images/process/step4-55cfd8.png'
      }
    ];

    return {
      processSteps
    };
  }
});
</script>

<style lang="scss" scoped>
.figma-process-section {
  padding: 2.55%; // Adjusted from 49px/1920px, 385px/1920px, 50px/1920px
  background-color: #FFFFFF;
  width: 100%;
  max-width: 1200px;

  .figma-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 50px;
    padding: 0px 10px;
    width: 100%;
  }


  .figma-header-section {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: space-between;
    gap: 191.67px;
    width: 100%;
    background-color: #FFFFFF;
  }

  .figma-header-left {
    display: flex;
    flex-direction: column;
    gap: 48px;
    padding: 0px 10px;
  }

  .figma-header-title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 600;
    font-size: 32px;
    line-height: 1.2em;
    letter-spacing: 0.03125em; // 3.125%
    text-transform: uppercase; // TITLE case
    text-align: left;
    background: linear-gradient(to right, #26BCEE, #0067B2);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
  }

  .figma-header-description {
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    font-size: 15px;
    line-height: 1.6em;
    text-align: left;
    color: #2B2B2B;
    width: 100%; // Adjusted from 555px / 1150px (parent width)
    max-width: 555px;
  }

  .figma-header-right {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 48px;
    padding: 0px 10px;
    height: auto;
  }

  .figma-design-text {
    font-family: 'Montserrat', sans-serif;
    font-weight: 600;
    font-size: 32px;
    line-height: 1.218999981880188em;
    text-align: right;
    color: #2B2B2B;
    background-image: linear-gradient(-225deg,#c00000 0%,#a11eff 29%,#39be07 67%,#ffd95d 100%);
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: #fff0;    
    animation: textclip 2s linear infinite;
  }

  @keyframes textclip {
    100% {
      background-position: 200% center;
    }
  }

  .figma-buttons-wrapper {
    display: flex;
    gap: 10px;
  }

  .figma-button-prev,
  .figma-button-next {
    width: 36px;
    height: 35px;
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;

    img {
      width: 100%;
      height: 100%;
    }
  }  

  .figma-process-list {
    display: flex;
    flex-direction: row;
    width: 100%; // Adjusted from 1132px / 1150px (parent width)
    max-width: 1132px;
  }

  .figma-process-item {
    display: flex;
    flex-direction: column;
    padding: 0px 11.5px;
    width: 25%; // Adjusted from 283px / 1132px (parent width)
    height: auto; // Use auto for height to maintain aspect ratio
    // position: relative;

    &__content {
      // position: relative;
      width: 100%;
      height: auto; // Use auto for height to maintain aspect ratio
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    &__description {
      // position: absolute;
      top: 420.23px;
      left: 0;
      width: 91.87%; // Adjusted from 260px / 283px (parent width)
      max-width: 260px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 400;
      font-size: 14px;
      line-height: 1.7142857142857142em;
      text-align: left;
      color: #2B2B2B;
    }

    &__image {
      // position: absolute;
      top: 0;
      left: 0;
      width: 91.87%; // Adjusted from 260px / 283px (parent width)
      height: auto; // Use auto for height to maintain aspect ratio
      overflow: hidden;
      border-radius: 20px 0px 20px 0px;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    &__gradient {
      // position: absolute;
      top: 0;
      left: -274.33px; // Adjusted based on Figma data
      width: 102%; // Adjusted from 288.66px / 283px (parent width)
      height: auto; // Use auto for height to maintain aspect ratio
      background: linear-gradient(to right, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.3) 100%);
    }

    &__info {
      position: relative;
      display: flex;
      align-items: center;
      gap: 0;
      padding: 0px 0px 14px;
      width: 91.87%; // Adjusted from 260px / 283px (parent width)
      max-width: 260px;

      &::after {
        content: '';
        position: absolute;
        top: 39px; // Adjusted based on Figma data
        left: 0;
        width: 25%; // Adjusted from 65px / 260px (parent width)
        height: 5px;
        background: linear-gradient(to right, #F8A900 0%, #ED7304 100%);
      }      
    }

    &__title {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 16px;
      line-height: 1.5em;
      text-align: left;
      background: linear-gradient(to right, #474645 7.75%, #707070 91.83%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      color: transparent;
      flex-grow: 1;
    }

    &__number {
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
      font-size: 30px;
      line-height: 1em;
      text-align: left;
      color: #000000;
    }
  }

  // Adjustments for subsequent items based on Figma layout
  .figma-process-item:nth-child(even) {
    padding-top: 38px;
  }
}
</style>
