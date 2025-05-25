<template>
  <section class="contact-section">
    <div class="container">
      <div class="row">
        <div class="col medium-4 small-12 large-4">
          <div class="contact-item">
            <div class="icon-box">
              <i class="fas fa-headset"></i>
            </div>
            <div class="contact-text">
              <strong>Hỗ trợ kỹ thuật</strong>
              <a href="tel:0984966806">0984.966.806</a>
            </div>
          </div>
        </div>
        
        <div class="col medium-4 small-12 large-4">
          <div class="contact-item">
            <div class="icon-box">
              <i class="fas fa-microphone-alt"></i>
            </div>
            <div class="contact-text">
              <strong>Tư vấn Thiết kế website</strong>
              <a href="tel:0988609664">0988.609.664</a>
            </div>
          </div>
        </div>
        
        <div class="col medium-4 small-12 large-4">
          <div class="contact-item">
            <div class="icon-box">
              <i class="fas fa-envelope"></i>
            </div>
            <div class="contact-text">
              <strong>Gửi email hỗ trợ</strong>
              <a href="mailto:lienhe@tamnguyen.vn">lienhe@tamnguyen.vn</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
</script>

<style scoped lang="scss">
.contact-section {
  background-color: #4a00e0;
  padding: 30px 0;
  color: #fff;

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 15px;
    display: flex;
    justify-content: center;
  }

  .row {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    width: 100%;
  }

  .col {
    padding: 0 15px;
    margin-bottom: 20px;
    flex-basis: auto;
  }

  .contact-item {
    display: flex;
    align-items: center;
    transition: transform 0.3s ease;

    &:hover {
      transform: translateY(-5px);
    }
  }

  .icon-box {
    margin-right: 15px;
    font-size: 2.5em;
    color: #fff;
    
    i {
        line-height: 1; 
    }
  }

  .contact-text {
    display: flex;
    flex-direction: column;

    strong {
      font-size: 1em;
      margin-bottom: 5px;
      display: block;
      font-weight: 500;
    }

    a {
      color: #fff;
      text-decoration: none;
      font-size: 1.25em;
      font-weight: bold;
      transition: color 0.3s ease;

      &:hover {
        color: #f0f0f0;
      }
    }
  }

  @media (max-width: 992px) {
    .row {
        justify-content: center;
    }
    .col {
        margin-bottom: 25px;
        width: 100%;
        max-width: 300px;
        text-align: center;
    }
    .contact-item {
        flex-direction: column;
        align-items: center;
    }
    .icon-box {
        margin-right: 0;
        margin-bottom: 10px;
    }
  }

  @media (max-width: 768px) {
    .col {
      flex: 0 0 100%;
      max-width: 100%;
      margin-bottom: 20px;
    }
    .contact-item {
        flex-direction: row;
         align-items: center;
    }
     .icon-box {
        margin-right: 15px;
        margin-bottom: 0;
    }
    .contact-text {
      text-align: left;
      strong {
        font-size: 0.9em;
      }

      a {
        font-size: 1.1em;
      }
    }
  }
   @media (max-width: 480px) {
    .contact-item {
      flex-direction: column;
      align-items: center;
       text-align: center;
    }
    .icon-box {
      margin-right: 0;
      margin-bottom: 8px;
    }
     .contact-text {
       align-items: center;
     }
  }
}
</style> 