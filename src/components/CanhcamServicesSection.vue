<template>
  <section class="services-section">
    <div class="container">
      <div class="heading-container">
        <h3>Services</h3>
        <p>CanhCam Agency specializes in offering a comprehensive range of services precisely tailored to your business.</p>
      </div>
      <div class="services-grid">
        <div class="service-card">
          <div class="service-image" style="background-image: url('/images/services/wwebdesign-640x640.webp');"></div>
          <div class="service-gradient"></div>
          <div class="service-title-container">
            <h4>Website Design</h4>
            <div class="wrap-desc">
              <div class="desc-service text-xl mb-4 font-light">
                <p>Khám phá cách Công ty thiết kế website chuyên nghiệp Cánh Cam giúp khách hàng bán hàng trực tuyến hiệu quả và tạo ấn tượng thương hiệu tốt hơn thông qua chiến lược ưu việt dưới đây.</p>
              </div>
              <a class="btn btn-discover white" href="https://www.canhcam.vn/thiet-ke-website" title="Tìm hiểu thêm - Thiết Kế Website">Tìm hiểu thêm</a>
            </div>
          </div>
        </div>
        <div class="service-card">
          <div class="service-image" style="background-image: url('/images/services/ecomerce-webdesign-640x640.webp');"></div>
          <div class="service-gradient"></div>
          <div class="service-title-container">
            <h4>E-Commerce</h4>
            <div class="wrap-desc">
              <div class="desc-service">
                <p>Gia tăng doanh số bán hàng trên kênh online cũng như xây dựng vị thế trên thị trường của bạn với những giải pháp thương mại điện tử (TMĐT) hàng đầu. Đó là những gì dịch vụ thiết kế website của Cánh Cam mang lại.</p>
              </div>
              <a class="btn" href="#" title="Tìm hiểu thêm - Thiết Kế Website E-Commerce">Tìm hiểu thêm</a>
            </div>
          </div>
        </div>
        <div class="service-card">
          <div class="service-image" style="background-image: url('/images/services/wordpress-640x640.webp');"></div>
          <div class="service-gradient"></div>
          <div class="service-title-container">
            <h4>Mobile App Design</h4>
            <div class="wrap-desc">
              <div class="desc-service">
                <p>Thiết kế và lập trình chuyên nghiệp các ứng dụng di động và ứng dụng web (MVP), cung cấp các sản phẩm phần mềm phù hợp với nhu cầu chuyển đổi số và trải nghiệm thân thiện với&nbsp;người dùng.</p>
              </div>
              <a class="btn" href="#" title="Tìm hiểu thêm - Thiết Kế App Mobile">Tìm hiểu thêm</a>
            </div>
          </div>          
        </div>
        <div class="service-card">
          <div class="service-image" style="background-image: url('/images/services/mobileapp-640x640.webp');"></div>
          <div class="service-gradient"></div>
          <div class="service-title-container">
            <h4>Web Copywriting</h4>
            <div class="wrap-desc">
              <div class="desc-service text-xl mb-4 font-light">
                <p>Xây dựng nội dung website sáng tạo, thu hút và giữ chân khách hàng hiệu quả, đặc biệt từ khóa, nội dung được tối ưu chuẩn SEO giúp gia tăng thứ hạng trên công cụ tìm kiếm, bởi đội ngũ Copywriter dày dặn kinh nghiệm.</p>
              </div>
              <a class="btn btn-discover white" href="https://www.canhcam.vn/sang-tao-noi-dung" title="Tìm hiểu thêm - Sáng Tạo Nội Dung">Tìm hiểu thêm</a>
            </div>            
          </div>
        </div>
        <div class="service-card">
          <div class="service-image" style="background-image: url('/images/services/onlinemarketing-640x640.webp');"></div>
          <div class="service-gradient"></div>
          <div class="service-title-container">
            <h4>Advertising Campaign</h4>
            <div class="wrap-desc">
              <div class="desc-service text-xl mb-4 font-light">
                <p>Chiến dịch quảng cáo bám sát mục tiêu kinh doanh sẽ mang bạn đến gần khách hàng tiềm năng một cách nhanh chóng.</p>
              </div>
              <a class="btn btn-discover white" href="https://www.canhcam.vn/chien-dich-quang-cao" title="Tìm hiểu thêm - Chiến Dịch Quảng Cáo">Tìm hiểu thêm</a>
            </div>            
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ServicesSection',
});
</script>

<style scoped lang="scss">
.services-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 48px;
  padding: 80px 0px;
  width: 100%;
  background-color: #EFF2F4;
}

.container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  /* width: 1280px; */
  width: 100%;
  max-width: 100%;
  /* padding: 0 20px;  */
  box-sizing: border-box;
}

.heading-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

.heading-container h3 {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: 46.125px;
  line-height: 1.3em;
  text-align: center;
  color: #5D5866;
  margin-bottom: 20px;
}

.heading-container p {
  font-family: 'Inter', sans-serif;
  font-weight: 200;
  font-size: 23.0625px;
  line-height: 1.56em;
  text-align: center;
  color: #6F6875;
  max-width: 800px; /* Limit width for readability */
}

.services-grid {
  display: flex;
  flex-direction: row;
  justify-content: stretch;
  align-items: stretch;
  width: 100%;
  flex-wrap: wrap; /* Allow wrapping for responsiveness */
  /* gap: 20px; */

  &:has(.service-card:hover) .service-card:not(:hover) {
    &::before {
      background-color: rgba(0,0,0,.4);  
    }

    .service-title-container {
      opacity: 0;
    }
  }
}

.service-card {
  position: relative;
  display: flex;
  flex-direction: column;
  // width: calc(20% - 20px);
  height: 640px;
  overflow: hidden;
  flex-grow: 1; /* Allow cards to grow */
  width: auto;
  transition: all cubic-bezier(.4,0,.2,1) .7s;
  // min-width: 280px;

  &:hover {
    flex-grow: 2;

    .service-title-container {
      transform: translateY(0);
    }

    .wrap-desc {
      opacity: 1;
    }    
  }

  &::before {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(180deg,transparent,rgba(0,0,0,.8));
    background-color: transparent;
    transition: background-color cubic-bezier(.4,0,.2,1) 0.2s;
    content: "";
    z-index: 2;
  }

  &::after {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 50%;
    background: linear-gradient(180deg,transparent,rgba(0,0,0,.4));
    content: "";    
    z-index: 2;
  }
}

.service-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  z-index: 1;
}

.service-gradient {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50%; /* Adjusted to cover the bottom half */
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.8) 100%);
  z-index: 2;
}

.service-title-container {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 32px 40px;
  box-sizing: border-box;
  z-index: 3;
  color: white;
  opacity: 1;
  transform: translateY(calc(100% - 8.33333rem));
  transition-delay: .1s;
  transition-duration: .5s;
  transition-property: all;
  transition-timing-function: cubic-bezier(.4,0,.2,1);
  overflow: hidden;
  pointer-events: none; 
  
  .wrap-desc {
    opacity: 0;
    transition-delay: .3s;
    transition-duration: .5s;
    transition-property: all;
    transition-timing-function: cubic-bezier(.4,0,.2,1);

    .desc-service {
      font-weight: 300;
      font-size: 20px;
      margin-bottom: .83333rem;
    }

    .btn {
      height: 1.875rem;
      display: inline-block;
      position: relative;
      transform: translateZ(0) translateY(0);
      padding-top: .625rem;
      padding-bottom: .625rem;
      width: -moz-fit-content;
      width: fit-content;
      color: white;
      font-weight: 700;
      font-size: clamp(18px,1.04167rem,1.04167rem);
      line-height: .7692307692!important;
      text-decoration: none;

      &::before {
        display: block;
        position: absolute;
        bottom: 0;
        transform: translateZ(0) translateY(0);
        background-color: rgb(22 216 207);
        width: 100%;
        height: .20833rem;
        content: "";
      }
    }
  }
}

.service-title-container h4 {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: 31px;
  line-height: 1.55em;
  text-align: left;
  color: #FFFFFF;
  margin: 0;
}

/* Responsive adjustments */
@media (max-width: 1200px) {
  .container {
    width: 960px;
  }
  .service-card {
    width: calc(33.33% - 14px); /* 3 cards per row */
  }
}

@media (max-width: 768px) {
  .container {
    width: 100%;
  }
  .service-card {
    width: calc(50% - 10px); /* 2 cards per row */
  }
}

@media (max-width: 480px) {
  .service-card {
    width: 100%; /* 1 card per row */
  }
  .heading-container h3 {
    font-size: 36px;
  }
  .heading-container p {
    font-size: 18px;
  }
}
</style>