<template>
  <footer class="footer-section">
    <div class="background-overlay"></div>
    <div class="container main-footer-content">
      <div class="row">
        <div class="col large-3 medium-6 small-12 widget-area">
          <div class="footer-widget about-widget">
            <!-- <img src="/images/logo-tamnguyenmedia.png" alt="Tam Nguyen Media Logo" class="footer-logo" /> -->
            <p class="company-subtitle">Giúp khách hàng tìm thấy bạn nhanh nhất</p>
            <p class="company-description">
              Tam Nguyên Media Công ty chuyên thiết kế website, chăm sóc website, quảng cáo Google, SEO
            </p>
            <h3 class="connect-title">Kết nối với Tam Nguyên</h3>
            <div class="social-links">
              <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
              <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
              <a href="#" class="social-link"><i class="fab fa-pinterest"></i></a>
              <a href="#" class="social-link"><i class="fab fa-youtube"></i></a>
            </div>
          </div>
        </div>

        <div class="col large-3 medium-6 small-12 widget-area">
          <div class="footer-widget links-widget">
            <h3>Giới thiệu</h3>
            <ul class="footer-links">
              <li><a href="#">Về chúng tôi</a></li>
              <li><a href="#">Lý do lựa chọn</a></li>
              <li><a href="#">Quy trình thiết kế web</a></li>
              <li><a href="#">Hình thức thanh toán</a></li>
              <li><a href="#">Liên hệ</a></li>
            </ul>
          </div>
        </div>

        <div class="col large-3 medium-6 small-12 widget-area">
          <div class="footer-widget links-widget">
            <h3>Dịch vụ</h3>
            <ul class="footer-links">
              <li><a href="#">Dịch vụ nâng cấp website</a></li>
              <li><a href="#">Dịch vụ chăm sóc website</a></li>
              <li><a href="#">Dịch vụ quản trị website</a></li>
              <li><a href="#">Dịch vụ SEO tổng thể</a></li>
              <li><a href="#">Dịch vụ quảng cáo Google</a></li>
              <li><a href="#">Dịch vụ tối ưu website</a></li>
            </ul>
          </div>
        </div>

        <div class="col large-3 medium-6 small-12 widget-area">
          <div class="footer-widget links-widget">
            <h3>Thông tin khác</h3>
            <ul class="footer-links">
              <li><a href="#">Chính sách bảo mật</a></li>
              <li><a href="#">Chính sách điều khoản</a></li>
              <li><a href="#">Điều khoản sử dụng</a></li>
              <li><a href="#">Xoá cache máy tính</a></li>
              <li><a href="#">Cài đặt Remote Desktop</a></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-contact-details">
        <div class="container">
            <p class="company-name-footer">TAM NGUYÊN MEDIA</p>
            <p>Địa chỉ: Tầng 2A tòa 27A3 Greenstars Phạm Văn Đồng, Bắc Từ Liêm, Hà Nội</p>
            <p>Điện thoại: 0984.966.806 - Email: lienhe@tamnguyen.vn</p>
        </div>
    </div>
    <div class="footer-bottom">
      <div class="container">
        <p>Copyright 2025 &copy; <strong>Tam Nguyên Media</strong></p>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
// Component logic here if needed
</script>

<style scoped lang="scss">
.footer-section {
  background-color: #1c1c1c; // Darker background as per image
  color: #a9a9a9; // Lighter grey for text
  padding: 60px 0 0;
  position: relative;
  overflow: hidden;

  .background-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url('/images/footer-bg-pattern.png'); // Path to your background pattern
    background-repeat: repeat;
    opacity: 0.05; // Subtle pattern
    z-index: 0;
  }

  .main-footer-content {
      position: relative; /* Ensure content is above overlay */
      z-index: 1;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 15px;
  }

  .row {
    display: flex;
    flex-wrap: wrap;
    margin: 0 -15px;
  }

  .col.widget-area {
    padding: 0 15px;
    margin-bottom: 40px;
  }

  .footer-widget {
    h3 {
      font-size: 1.1em; // Slightly smaller heading
      color: #fff; // White headings
      margin-bottom: 25px;
      position: relative;
      padding-bottom: 10px;
      font-weight: 600;

      &:after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 30px; // Shorter underline
        height: 2px;
        background-color: #007bff; // Blue accent
      }
    }
  }

  .about-widget {
    .footer-logo {
      max-width: 220px; // Adjusted logo size
      margin-bottom: 10px;
    }
    .company-subtitle {
        font-size: 0.85em;
        color: #f0f0f0; // Bright subtitle
        margin-bottom: 15px;
        font-style: italic;
    }
    .company-description {
        font-size: 0.9em;
        line-height: 1.6;
        margin-bottom: 20px;
    }
    .connect-title {
        font-size: 1em;
        color: #fff;
        margin-top: 20px;
        margin-bottom: 15px;
         &:after {
            display: none; // Remove underline for this specific h3
        }
    }
  }

  .social-links {
    display: flex;
    gap: 10px; // Smaller gap

    .social-link {
      width: 30px; // Smaller icons
      height: 30px;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.08);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #a9a9a9;
      font-size: 0.9em;
      transition: all 0.3s ease;

      &:hover {
        background-color: #007bff;
        color: #fff;
        transform: translateY(-2px);
      }
    }
  }

 .links-widget {
     ul.footer-links {
        padding-left: 0; // Remove default padding
     }
 }

  .footer-links {
    list-style: none;
    padding: 0;
    margin: 0;

    li {
      margin-bottom: 12px; // Increased spacing

      a {
        color: #a9a9a9;
        text-decoration: none;
        transition: color 0.3s ease, padding-left 0.3s ease;
        position: relative;
        font-size: 0.9em;
        padding-left: 18px; // Space for icon

        &:before {
          content: '\f054'; // Font Awesome chevron right
          font-family: 'Font Awesome 6 Free';
          font-weight: 900;
          position: absolute;
          left: 0;
          top: 1px;
          transition: color 0.3s ease;
          color: #007bff;
        }

        &:hover {
          color: #fff; // White on hover
          padding-left: 22px; // Move text slightly
          &:before{
            color: #fff;
          }
        }
      }
    }
  }

  .footer-contact-details {
    text-align: center;
    padding: 20px 0;
    color: #a9a9a9;
    font-size: 0.9em;
    position: relative;
    z-index: 1;
    border-top: 1px solid rgba(255,255,255,0.1);
    margin-top: 20px; /* Spacing from widget area */

    .company-name-footer {
        font-size: 1.1em;
        font-weight: bold;
        color: #fff;
        margin-bottom: 10px;
    }

    p {
        margin-bottom: 5px;
        line-height: 1.7;
    }
  }

  .footer-bottom {
    background-color: #111; // Darker bottom bar
    padding: 15px 0;
    text-align: center;
    position: relative;
    z-index: 1;

    p {
      margin: 0;
      color: #888; // Darker grey for copyright
      font-size: 0.85em;
      strong {
          color: #fff; // White for company name in copyright
          font-weight: 500;
      }
    }
  }

  @media (max-width: 992px) {
    .col.large-3.widget-area {
      flex: 0 0 50%;
      max-width: 50%;
    }
  }

  @media (max-width: 768px) {
    .col.large-3.widget-area {
      flex: 0 0 100%;
      max-width: 100%;
      text-align: center; /* Center align widget content */
    }

    .footer-widget h3:after {
      left: 50%;
      transform: translateX(-50%);
    }
    
    .about-widget .footer-logo {
        margin-left: auto;
        margin-right: auto;
    }

    .social-links {
      justify-content: center;
    }

    .footer-links li a {
        padding-left: 25px; /* Adjust for centered text */
         &:before {
            left: 5px; /* Adjust icon for centered text */
        }
        &:hover {
             padding-left: 30px;
        }
    }
  }
}
</style> 