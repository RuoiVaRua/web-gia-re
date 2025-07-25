<script setup lang="ts">
import { ref } from 'vue';

interface MenuItem {
  id: string;
  label: string;
  href?: string;
  children?: SubMenuItem[];
  megaMenu?: MegaMenuItem[];
}

interface SubMenuItem {
  id: string;
  label: string;
  href: string;
  description?: string;
}

interface MegaMenuItem {
  id: string;
  title: string;
  items: SubMenuItem[];
}

const menuOpen = ref(false);
const activeMenu = ref<string | null>(null);

const menuItems: MenuItem[] = [
  {
    id: 'customer',
    label: 'Customer',
    megaMenu: [
      {
        id: 'customer-main',
        title: 'Join the growing community of businesses who trust our solutions to drive sustainable growth and stay ahead of the curve.',
        items: [
          { id: 'customer-stories', label: 'Customer Stories', href: '#', description: '' }
        ]
      },
      {
        id: 'customer-categories',
        title: '',
        items: [
          { id: 'banking', label: 'Banking', href: '#', description: 'Tailored solutions for every bank, every sector' },
          { id: 'financial-services', label: 'Financial Services', href: '#', description: 'Conquer the era of privacy & digital-first in financial industry' },
          { id: 'retail', label: 'Retail', href: '#', description: 'Grow customer loyalty and build brand love for your business' },
          { id: 'hospitality', label: 'Hospitality', href: '#', description: 'Transform guest stays into memorable experience' },
          { id: 'healthcare', label: 'Healthcare', href: '#', description: 'Optimize customer journey to heal the pain of healthcare services' },
        ]
      }
    ]
  },
  {
    id: 'solution',
    label: 'Solution',
    megaMenu: [
      {
        id: 'solution-main',
        title: 'Mobio crafts solutions across industries, from streamlining processes to boosting engagement, we help businesses thrive.',
        items: [
          { id: 'solution-overview', label: 'Overview', href: '#', description: '' }
        ]
      },
      {
        id: 'solution-products',
        title: '',
        items: [
          { id: 'activation-cdp', label: 'Activation CDP', href: '#', description: 'Meet the goals of every marketer with a comprehensive platform' },
          { id: 'smart-crm', label: 'Smart CRM', href: '#', description: 'Elevate sales, delight service for customer satisfaction' },
          { id: 'adp', label: 'Analytics Data Platform (ADP)', href: '#', description: 'Get the most ouf of your data for smarter business decisions' },
        ]
      }
    ]
  },
  { id: 'pricing', label: 'Pricing', href: '#' },
  {
    id: 'library',
    label: 'Library',
    megaMenu: [
       {
        id: 'library-main',
        title: 'Get inspired with success stories from customers and businesses just like yours.',
        items: [
          { id: 'library-whats-new', label: "What's new?", href: '#', description: '' }
        ]
      },
      {
        id: 'library-resources',
        title: '',
        items: [
          { id: 'knowledge', label: 'Knowledge', href: '#', description: 'Discover the secrets to success with our knowledge base' },
          { id: 'product', label: 'Product', href: '#', description: 'See how Mobio can help your business to achieve more' },
          { id: 'news-events', label: 'News & Events', href: '#', description: 'Stay ahead of the curve with the latest industry insights and events' },
          { id: 'use-cases', label: 'Use cases', href: '#', description: '50+ use cases to overcome real-world challenges' },
          { id: 'help-center', label: 'Help Center', href: '#', description: 'Find quick and easy answers to all your questions about Mobio' },
        ]
      }
    ]
  },
  {
    id: 'about-us',
    label: 'About Us',
    megaMenu: [
      {
        id: 'about-main',
        title: 'We\'re just getting started, and we\'re so grateful for all our trusted tenants and partners that are joining in this journey with us.',
        items: [
          { id: 'about-welcome', label: 'Welcome to Mobio', href: '#', description: '' }
        ]
      },
      {
        id: 'about-company',
        title: '',
        items: [
          { id: 'our-story', label: 'Our Story', href: '#', description: 'Dive into the 7 years of innovation behind our success' },
          { id: 'career', label: 'Career', href: '#', description: 'Join our team and explore exciting career opportunities' },
          { id: 'partners', label: 'Partners', href: '#', description: 'Learn how partnering with us can fuel mutual growth' },
        ]
      }
    ]
  },
];

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};

const showMegaMenu = (menuId: string) => {
  activeMenu.value = menuId;
};

const hideMegaMenu = () => {
  activeMenu.value = null;
};
</script>

<template>
  <nav class="mobio-nav">
    <div class="nav-container">
      <div class="logo">
        <a href="https://mobio.io/">
          <img src="/webest.png" alt="Mobio Logo" class="logo-normal">
          <img src="/webest.png" alt="Mobio Logo Fixed" class="logo-fixed">
        </a>
      </div>
      <div class="menu-toggle" @click="toggleMenu">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
        </svg>
      </div>
      <ul class="nav-links" :class="{ open: menuOpen }">
        <li 
          v-for="item in menuItems" 
          :key="item.id"
          @mouseenter="item.megaMenu ? showMegaMenu(item.id) : null"
          @mouseleave="item.megaMenu ? hideMegaMenu() : null"
          class="nav-item"
          :class="{ 'has-mega-menu': item.megaMenu }"
        >
          <a :href="item.href || '#'" class="nav-link">{{ item.label }}
             <svg v-if="item.megaMenu" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5 inline-block ml-1 opacity-70">
                <path fill-rule="evenodd" d="M5.22 8.22a.75.75 0 0 1 1.06 0L10 11.94l3.72-3.72a.75.75 0 1 1 1.06 1.06l-4.25 4.25a.75.75 0 0 1-1.06 0L5.22 9.28a.75.75 0 0 1 0-1.06Z" clip-rule="evenodd" />
            </svg>
          </a>
          <div 
            v-if="item.megaMenu && activeMenu === item.id" 
            class="mega-menu-container"
            @mouseenter="showMegaMenu(item.id)" 
            @mouseleave="hideMegaMenu()"
          >
            <div class="mega-menu-content">
              <div v-for="section in item.megaMenu" :key="section.id" class="mega-menu-section">
                <h4 v-if="section.title">{{ section.title }}</h4>
                <ul>
                  <li v-for="subItem in section.items" :key="subItem.id" class="mega-menu-item">
                    <a :href="subItem.href">
                      <span>{{ subItem.label }}</span>
                      <small v-if="subItem.description">{{ subItem.description }}</small>
                    </a>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </li>
      </ul>
      <div class="nav-actions">
        <a href="#" class="brochure-btn">BROCHURE</a>
        <a href="#" class="contact-btn">Contact sales</a>
      </div>
    </div>
  </nav>
</template>

<style scoped lang="scss">
.mobio-nav {
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  padding: 0 20px;
  position: sticky;
  top: 0;
  z-index: 1000;
  font-family: 'Inter', sans-serif; /* As seen on Mobio */

  .nav-container {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 70px; /* Typical header height */
  }

  .logo {
    display: flex;
    align-items: center;
    img {
      height: 30px; /* Adjust as needed */
    }
    .logo-fixed { display: none; } /* Logic for showing fixed logo on scroll would be in parent or via JS */
  }

  .nav-links {
    list-style: none;
    display: flex;
    align-items: center;
    margin: 0;
    padding: 0;

    .nav-item {
      position: relative; /* For mega menu positioning */
      padding: 0 15px;

      .nav-link {
        text-decoration: none;
        color: #333;
        font-weight: 500;
        font-size: 15px;
        padding: 25px 0; /* To make clickable area larger and align with hover */
        display: flex;
        align-items: center;
        transition: color 0.3s ease;

        &:hover {
          color: #007bff; /* Mobio's primary blue */
        }
      }

      &.has-mega-menu .nav-link:hover {
         border-bottom: 2px solid #007bff; /* Underline effect for active menu item */
      }
    }
  }

  .mega-menu-container {
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #fff;
    box-shadow: 0 8px 16px rgba(0,0,0,0.1);
    border-radius: 0 0 8px 8px;
    padding: 30px;
    width: auto; /* Adjust based on content, can be fixed */
    min-width: 600px; /* Example minimum width */
    opacity: 0;
    visibility: hidden;
    transform: translateY(10px);
    transition: opacity 0.3s ease, transform 0.3s ease, visibility 0.3s ease;
    display: flex; /* Keep it as flex for inner content */
  }

  .nav-item:hover .mega-menu-container,
  .mega-menu-container:hover { /* Keep visible when hovering over mega menu itself */
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
  }

  .mega-menu-content {
    display: flex;
    gap: 40px; /* Space between sections */
    width: 100%;
  }

  .mega-menu-section {
    flex: 1;
    h4 {
      font-size: 14px;
      color: #555;
      margin-bottom: 15px;
      font-weight: normal;
      line-height: 1.4;
      max-width: 250px; /* For the description-like titles */
    }
    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .mega-menu-item {
      margin-bottom: 10px;
      a {
        text-decoration: none;
        color: #333;
        display: block;
        padding: 8px 12px;
        border-radius: 4px;
        transition: background-color 0.2s ease, color 0.2s ease;

        &:hover {
          background-color: #f0f8ff; /* Light blue hover */
          color: #007bff;
        }
        span {
          font-weight: 500;
          font-size: 15px;
          display: block;
          margin-bottom: 2px;
        }
        small {
          font-size: 12px;
          color: #777;
          display: block;
        }
      }
    }
  }

  .nav-actions {
    display: flex;
    align-items: center;
    .brochure-btn, .contact-btn {
      text-decoration: none;
      padding: 8px 16px;
      border-radius: 20px;
      font-weight: 500;
      font-size: 14px;
      transition: background-color 0.3s ease, color 0.3s ease;
      margin-left: 10px;
    }
    .brochure-btn {
      border: 1px solid #007bff;
      color: #007bff;
      &:hover {
        background-color: #007bff;
        color: #fff;
      }
    }
    .contact-btn {
      background-color: #007bff;
      color: #fff;
      border: 1px solid #007bff;
      &:hover {
        background-color: #0056b3; /* Darker blue */
        border-color: #0056b3;
      }
    }
  }

  .menu-toggle {
    display: none; /* Hidden on desktop */
    cursor: pointer;
    svg {
      width: 28px;
      height: 28px;
      color: #333;
    }
  }

  /* Responsive adjustments */
  @media (max-width: 1024px) { /* Tablet and mobile */
    .nav-links {
      display: none; /* Hide normal links */
      position: absolute;
      top: 70px; /* Below header */
      left: 0;
      width: 100%;
      background-color: #fff;
      flex-direction: column;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      padding: 10px 0;

      &.open {
        display: flex; /* Show when toggled */
      }

      .nav-item {
        width: 100%;
        padding: 0;
        text-align: left;

        .nav-link {
          padding: 15px 20px;
          width: 100%;
          border-bottom: 1px solid #eee;
           &:hover {
             border-bottom: 1px solid #eee; /* Remove underline on hover for mobile */
           }
        }
        &.has-mega-menu .nav-link:hover {
         border-bottom: 1px solid #eee; 
      }
      }
    }

    .mega-menu-container { /* Full width mega menu on mobile */
      position: static; /* No longer absolute */
      box-shadow: none;
      opacity: 1;
      visibility: visible;
      transform: none;
      padding: 10px 20px 20px 40px; /* Indent sub-items */
      border-top: 1px solid #eee;
      border-bottom: 1px solid #eee;
      min-width: unset;
      width: 100%;
      display: block; /* Stack sections vertically */

      .mega-menu-content{
        flex-direction: column;
        gap: 15px;
      }
       .mega-menu-section h4 {
         margin-bottom: 10px;
         max-width: 100%;
       }
    }
    
    .nav-item:hover .mega-menu-container { /* Ensure it's always visible when item active */
        opacity: 1;
        visibility: visible;
        transform: translateY(0);
    }

    .nav-item .nav-link svg { /* Arrow for dropdown */
        transition: transform 0.3s ease;
    }
    .nav-item.has-mega-menu .nav-link[aria-expanded="true"] svg {
        transform: rotate(180deg);
    }


    .nav-actions {
      .brochure-btn { display: none; } /* Optionally hide brochure on smaller screens */
    }
    .menu-toggle {
      display: block;
    }
  }
   @media (max-width: 767px) {
     .nav-actions .contact-btn {
       padding: 6px 12px;
       font-size: 13px;
     }
     .logo img {
       height: 25px;
     }
   }
}
</style> 