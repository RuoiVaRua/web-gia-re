<template>
  <section class="faq-section">
    <div class="faq-section__content-wrapper">
      <div class="faq-section__header">
        <div class="faq-section__heading-container">
          <div class="faq-section__mask-group">
            <!-- <div class="faq-section__mask"></div> -->
            <h4 class="faq-section__sub-heading">FAQ - MYPAGE</h4>
          </div>
          <h2 class="faq-section__main-heading">Các câu hỏi thường gặp</h2>
          <div class="faq-section__description-container">
            <p class="faq-section__description-mypage">MYPAGE</p>
            <p class="faq-section__description-text">
              giúp bạn giải đáp các thắc mắc hay gặp trong quá trình tìm kiếm
              <span class="faq-section__description-strong">đơn vị </span>
              <span class="faq-section__description-link">thiết kế website</span>
              và đồng hành cùng bạn suốt quá trình website hoạt động.
            </p>
          </div>
        </div>
      </div>

      <div class="faq-section__accordion-container">
        <div class="faq-item" :class="{ 'is-open': activeIndex === 0 }">
          <div class="faq-item__header" @click="toggleAccordion(0)">
            <h4 class="faq-item__question">Thiết kế web có bị tính thuế VAT không?</h4>
            <div class="faq-item__toggle-button">+</div>
          </div>
          <div class="faq-item__content">
            <p class="faq-item__answer">
              Theo pháp luật Việt Nam hiện nay thì thiết kế website không bị tính thuế VAT. Quý khách sẽ nhận được
              hóa đơn đúng với giá trị thanh toán mà không cần phải bù thêm khoảng phí nào.
            </p>
          </div>
        </div>

        <div class="faq-item" :class="{ 'is-open': activeIndex === 1 }">
          <div class="faq-item__header" @click="toggleAccordion(1)">
            <h4 class="faq-item__question">Mất bao lâu để hoàn thiện một website?</h4>
            <div class="faq-item__toggle-button">+</div>
          </div>
          <div class="faq-item__content">
            <!-- Content for this FAQ item -->
          </div>
        </div>

        <div class="faq-item" :class="{ 'is-open': activeIndex === 2 }">
          <div class="faq-item__header" @click="toggleAccordion(2)">
            <h4 class="faq-item__question">Tôi có thể đề nghị chỉnh sửa website sau khi hoàn thành không?</h4>
            <div class="faq-item__toggle-button">+</div>
          </div>
          <div class="faq-item__content">
            <!-- Content for this FAQ item -->
          </div>
        </div>

        <div class="faq-item" :class="{ 'is-open': activeIndex === 3 }">
          <div class="faq-item__header" @click="toggleAccordion(3)">
            <h4 class="faq-item__question">Tôi không biết lập trình có thể tự quản trị website không?</h4>
            <div class="faq-item__toggle-button">+</div>
          </div>
          <div class="faq-item__content">
            <!-- Content for this FAQ item -->
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const activeIndex = ref<number | null>(0); // Mở mục đầu tiên theo mặc định

const toggleAccordion = (index: number) => {
  activeIndex.value = activeIndex.value === index ? null : index;
};
</script>

<style lang="scss" scoped>
.faq-section {
  display: flex;
  flex-direction: column;
  padding: 60px 0 110px;
  width: 100%;
  position: relative;
  overflow: hidden;
  background-color: #FFFFFF;

  &__background-image-right {
    position: absolute;
    right: 310px; // 1920 - 1480 = 440, 440 - 310 (padding) = 130. Figma x: 1480, width: 480.
    top: 442px;
    width: 480px;
    height: 400px;
    background-image: url('/public/images/ngonshare/sec-8-anh-1-56586a.png'); // Assuming this is the correct image
    background-size: cover;
    opacity: 0.05;
  }

  &__background-image-left {
    position: absolute;
    left: 0; // Figma x: -150, width: 300.
    top: 0;
    width: 300px;
    height: 300px;
    background-image: url('/public/images/ngonshare/sec-8-anh-2-56586a.png'); // Assuming this is the correct image
    background-size: cover;
    opacity: 0.1;
  }

  &__content-wrapper {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: stretch;
    align-items: stretch;
    width: 100%;
  }

  &__header {
    display: flex;
    flex-direction: column;
    padding: 0 15px;
    width: 100%;
  }

  &__heading-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    gap: -30px; // Figma gap
    padding-bottom: 20px;
  }

  &__main-heading {
    font-family: 'Inter', sans-serif;
    font-weight: 700;
    font-size: 28.125px;
    line-height: 1.35em;
    text-align: center;
    color: #008ACD;
    width: 100%;
  }

  &__mask-group {
    position: relative;
    width: 100%;
    height: 120px;
    display: flex;
    justify-content: center;
    align-items: center;
    mask-image: linear-gradient(to bottom,#000 0,#00000033 100%);
  }

  &__mask {
    position: absolute;
    width: 100%;
    height: 100%;
    background: linear-gradient(to bottom, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, 0.2) 100%);
    opacity: 0.1;
  }

  &__sub-heading {
    font-family: 'Inter', sans-serif;
    font-weight: 700;
    font-size: 121.3671875px;
    line-height: 0.988em;
    letter-spacing: 0.8239459285484391px;
    text-align: center;
    color: rgba(119, 119, 119, 0.1);
    position: relative;
    z-index: 1;
  }

  &__description-container {
    width: 750px;
    height: 63px;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__description-mypage {
    // position: absolute;
    // left: 2.38px;
    // top: 0.5px;
    width: 70.61px;
    height: 28px;
    font-family: 'Inter', sans-serif;
    font-weight: 700;
    font-size: 16.453125px;
    line-height: 1.7018em;
    text-align: center;
    color: #000000;
  }

  &__description-text {
    // position: absolute;
    // left: 72.78px;
    // top: 0px;
    width: 498.51px;
    height: 28px;
    font-family: 'Inter', sans-serif;
    font-weight: 400;
    font-size: 16.3125px;
    line-height: 1.7164em;
    text-align: center;
    color: #000000;
  }

  &__description-strong {
    font-family: 'Inter', sans-serif;
    font-weight: 700;
    font-size: 17.4375px;
    line-height: 1.6057em;
    text-align: center;
    color: #000000;
  }

  &__description-link {
    font-family: 'Inter', sans-serif;
    font-weight: 700;
    font-size: 15.890625px;
    line-height: 1.762em;
    text-align: center;
    color: #195E94;
  }

  &__accordion-container {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding-top: 65px;
    width: 870px;
    margin: 0 auto; // Center the accordion container
  }
}

.faq-item {
  display: flex;
  flex-direction: column;
  border-radius: 5px;
  box-shadow: 0px 5px 15px 0px rgba(0, 0, 0, 0.1);
  background-color: rgba(255, 255, 255, 0); // Transparent background for the item itself

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 25px 30px;
    background: linear-gradient(to right, #D1F0FF 0%, #F4FDF9 100%);
    border-radius: 5px 5px 0px 0px;
    cursor: pointer;
  }

  &__question {
    font-family: 'Inter', sans-serif;
    font-weight: 700;
    font-size: 17.8125px;
    line-height: 1.6842em;
    text-align: left;
    color: #000000;
    margin: 0;
  }

  &__toggle-button {
    width: 30px;
    height: 30px;
    background-color: #23C1E5;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: 'Font Awesome 5 Free', sans-serif;
    font-weight: 900;
    font-size: 20.0000057220459px;
    line-height: 1.6em;
    color: #FFFFFF;
    transition: transform 0.3s ease;
  }

  &.is-open &__toggle-button {
    transform: rotate(45deg); // Rotate to form an 'X' or close icon
  }

  &__content {
    // display: none; // Hidden by default
    
    background-color: #F9FFF4;
    border-radius: 0 0 5px 5px; // Rounded bottom corners when open
    height: 0px;
    padding: 0 30px;
    transition: height 0.3s ease, padding 0.3s ease;
  }

  &.is-open &__content {
    height: 125px;
    padding: 15px 30px 25px;
  }

  &__answer {
    display: none;
    font-family: 'Inter', sans-serif;
    font-weight: 400;
    font-size: 16.171875px;
    line-height: 1.7314em;
    text-align: left;
    color: #000000;
    margin: 0;
  }

  &.is-open &__answer {
    display: block; // Show the answer when open
  }
}
</style>
