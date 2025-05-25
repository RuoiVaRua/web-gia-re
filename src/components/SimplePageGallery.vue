<script setup lang="ts">
import { ref, computed } from 'vue';

interface Category {
  id: string;
  name: string;
  desktopImage: string;
  mobileImage: string;
}

const categories: Category[] = [
  // Placeholder data - to be replaced with actual data from simplepage.json or user
  { id: 'bds', name: 'Bất động sản', desktopImage: 'https://via.placeholder.com/800x600?text=BDS+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=BDS+Mobile' },
  { id: 'ban-hang', name: 'Bán hàng', desktopImage: 'https://via.placeholder.com/800x600?text=Ban+Hang+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=Ban+Hang+Mobile' },
  { id: 'dich-vu', name: 'Dịch vụ', desktopImage: 'https://via.placeholder.com/800x600?text=Dich+Vu+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=Dich+Vu+Mobile' },
  { id: 'giao-duc', name: 'Giáo dục', desktopImage: 'https://via.placeholder.com/800x600?text=Giao+Duc+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=Giao+Duc+Mobile' },
  { id: 'tai-chinh', name: 'Tài chính', desktopImage: 'https://via.placeholder.com/800x600?text=Tai+Chinh+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=Tai+Chinh+Mobile' },
  { id: 'cv-bio', name: 'CV & Bio', desktopImage: 'https://via.placeholder.com/800x600?text=CV+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=CV+Mobile' },
  { id: 'my-pham', name: 'Mỹ phẩm', desktopImage: 'https://via.placeholder.com/800x600?text=My+Pham+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=My+Pham+Mobile' },
  { id: 'xe-o-to', name: 'Xe ô tô', desktopImage: 'https://via.placeholder.com/800x600?text=Xe+O+To+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=Xe+O+To+Mobile' },
  { id: 'game-app', name: 'Game - App', desktopImage: 'https://via.placeholder.com/800x600?text=Game+App+Desktop', mobileImage: 'https://via.placeholder.com/150x300?text=Game+App+Mobile' },
];

const activeCategoryId = ref<string>(categories[0]?.id || '');

const activeCategory = computed(() => {
  return categories.find(cat => cat.id === activeCategoryId.value);
});

function selectCategory(categoryId: string) {
  activeCategoryId.value = categoryId;
}
</script>

<template>
  <div class="simple-page-gallery">
    <div class="gallery-header">
      <h2>Mẫu giao diện landing page tại Simple Page</h2>
      <p>Hơn 1000 mẫu giao diện Việt Hóa trên nhiều lĩnh vực được cập nhật mỗi ngày.</p>
    </div>
    <div class="gallery-content">
      <div class="category-list">
        <ul>
          <li
            v-for="category in categories"
            :key="category.id"
            :class="{ active: category.id === activeCategoryId }"
            @click="selectCategory(category.id)"
          >
            {{ category.name }}
          </li>
        </ul>
      </div>
      <div class="image-preview-area">
        <div v-if="activeCategory" class="image-mockups">
          <div class="desktop-mockup">
            <img :src="activeCategory.desktopImage" :alt="activeCategory.name + ' Desktop Preview'" />
            <div class="browser-bar">
              <span class="dot"></span><span class="dot"></span><span class="dot"></span>
            </div>
          </div>
          <div class="mobile-mockup">
            <img :src="activeCategory.mobileImage" :alt="activeCategory.name + ' Mobile Preview'" />
            <div class="speaker"></div>
            <div class="home-button"></div>
          </div>
        </div>
        <div v-else class="no-preview">
          <p>Select a category to see the preview.</p>
        </div>
      </div>
    </div>
    <div class="gallery-footer">
      <button class="cta-button">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 btn-icon">
          <path stroke-linecap="round" stroke-linejoin="round" d="M2.036 12.322a1.012 1.012 0 0 1 0-.639l4.418-5.58a1.012 1.012 0 0 1 1.591 0l4.418 5.58a1.012 1.012 0 0 1 0 .639l-4.418 5.58a1.012 1.012 0 0 1-1.591 0l-4.418-5.58Z" />
          <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 12h-15" />
        </svg>
        Xem kho mẫu giao diện
      </button>
    </div>
  </div>
</template>

<style scoped lang="scss">
.simple-page-gallery {
  font-family: 'Roboto', sans-serif; // Assuming Roboto, common on Vietnamese sites
  color: #333;
  padding: 40px 20px;
  max-width: 1200px;
  margin: 0 auto;
  background-color: #f9f9f9; // Light gray background as seen in images

  .gallery-header {
    text-align: center;
    margin-bottom: 40px;
    h2 {
      font-size: 28px;
      font-weight: bold;
      margin-bottom: 10px;
      color: #2c3e50;
    }
    p {
      font-size: 16px;
      color: #555;
    }
  }

  .gallery-content {
    display: flex;
    gap: 30px;

    @media (max-width: 768px) {
      flex-direction: column;
    }
  }

  .category-list {
    flex: 0 0 200px; // Fixed width for category list
    ul {
      list-style: none;
      padding: 0;
      margin: 0;
      li {
        padding: 12px 15px;
        cursor: pointer;
        border-radius: 5px;
        margin-bottom: 8px;
        font-size: 15px;
        font-weight: 500;
        color: #34495e;
        transition: background-color 0.3s, color 0.3s;

        &:hover {
          background-color: #ecf0f1;
        }
        &.active {
          background-color: #ff6b00; // Orange accent from button
          color: white;
          font-weight: bold;
        }
      }
    }
  }

  .image-preview-area {
    flex: 1;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    padding: 20px;
    min-height: 500px; // Ensure it has some height
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative; // For mobile mockup positioning
  }

  .image-mockups {
    display: flex;
    align-items: flex-end; // Align mobile to bottom relative to desktop
    justify-content: center;
    gap: 10px; // Gap between desktop and mobile
    width: 100%;
    height: 100%;
    position: relative;

    .desktop-mockup {
      position: relative;
      width: 75%; // Adjust as needed
      max-width: 700px;
      aspect-ratio: 16/10; // Common desktop aspect ratio
      background-color: #e0e0e0; // Mockup background
      border-radius: 10px 10px 0 0; // Top corners rounded
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      padding-top: 25px; // Space for browser bar
      overflow: hidden;

      img {
        width: 100%;
        height: calc(100% - 25px); // Account for browser bar
        object-fit: cover;
        display: block;
      }

      .browser-bar {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 25px;
        background-color: #d0d0d0;
        display: flex;
        align-items: center;
        padding: 0 10px;
        border-bottom: 1px solid #bbb;

        .dot {
          height: 8px;
          width: 8px;
          border-radius: 50%;
          background-color: #bbb;
          margin-right: 5px;
          &:nth-child(1) { background-color: #ff5f57; } // Red
          &:nth-child(2) { background-color: #ffbd2e; } // Yellow
          &:nth-child(3) { background-color: #28c940; } // Green
        }
      }
    }

    .mobile-mockup {
      position: absolute;
      bottom: 20px; // Position from bottom
      right: 20px; // Position from right
      width: 20%; // Adjust as needed
      max-width: 150px;
      aspect-ratio: 9/19; // Common mobile aspect ratio
      background-color: #333; // Darker for phone
      border: 3px solid #444;
      border-radius: 20px;
      box-shadow: 0 5px 20px rgba(0,0,0,0.3);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 10px;
      overflow: hidden;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 10px; // Inner screen radius
      }
      
      .speaker {
        width: 30px;
        height: 3px;
        background-color: #555;
        border-radius: 2px;
        position: absolute;
        top: 12px; // Adjust if padding changes
        left: 50%;
        transform: translateX(-50%);
      }

      .home-button {
        width: 20px;
        height: 20px;
        background-color: #555;
        border-radius: 50%;
        position: absolute;
        bottom: 10px; // Adjust if padding changes
        left: 50%;
        transform: translateX(-50%);
        display: none; // Often hidden in modern designs or not distinctly visible
      }
    }
  }

  .no-preview p {
    font-size: 18px;
    color: #777;
  }

  .gallery-footer {
    text-align: center;
    margin-top: 40px;
    .cta-button {
      background-color: #ff6b00; // Orange color from image
      color: white;
      border: none;
      padding: 12px 30px;
      font-size: 16px;
      font-weight: bold;
      border-radius: 25px; // Pill shape
      cursor: pointer;
      transition: background-color 0.3s;
      display: inline-flex;
      align-items: center;
      gap: 8px;

      .btn-icon {
        width: 20px;
        height: 20px;
      }

      &:hover {
        background-color: #e65c00; // Darker orange on hover
      }
    }
  }
}
</style> 