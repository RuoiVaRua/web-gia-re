<template>
  <div class="header-menu">
    <div class="menu-list d-flex">
      <div class="menu-item menu-item-js"><a class="menu-item-link d-flex detect-link-js menu-mona-custom-link" href="https://mona.media/gioi-thieu/" data-wpel-link="internal"><span class="icon"><img src="https://mona.media/template/assets/images/header/icon-about.svg" alt=""></span><span class="txt">Giới thiệu</span></a></div>
      <div class="menu-item dropdown menu-item-js">
        <a class="menu-item-link d-flex menu-item-link-js detect-link-js menu-mona-custom-link" data-wpel-link="internal">
          <span class="icon">
            <img src="https://mona.media/template/assets/images/header/icon-service.svg" alt="">
          </span>
          <span class="txt">Dịch vụ</span>
          <span class="show-on-sp">
            <span class="dropdown-btn show-on-sp dropdown-btn-js">
              <img src="https://mona.media/template/assets/images/mega-menu-new/mega-menu-next.svg" alt="">
            </span>
          </span>
        </a>
        <!-- Full dropdown structure omitted for brevity but would be included in a real implementation -->
      </div>
      <div class="menu-item menu-item-js"><a class="menu-item-link d-flex detect-link-js menu-mona-custom-link" href="https://mona.media/du-an/" data-wpel-link="internal"><span class="icon"><img src="https://mona.media/template/assets/images/header/icon-project.svg" alt=""></span><span class="txt">Dự án</span></a></div>
      <div class="menu-item menu-item-js"><a class="menu-item-link d-flex detect-link-js menu-mona-custom-link" href="https://mona.media/khach-hang/" data-wpel-link="internal"><span class="icon"><img src="https://mona.media/template/assets/images/header/icon-customer.svg" alt=""></span><span class="txt">Khách hàng</span></a></div>
      <div class="menu-item dropdown dropdown-sub menu-item-js">
        <a class="menu-item-link d-flex detect-link-js menu-mona-custom-link" href="https://mona.media/blog/" data-wpel-link="internal">
          <span class="icon">
            <img src="https://mona.media/template/assets/images/header/icon-blog.svg" alt="">
          </span>
          <span class="txt">Blog</span>
        </a>
        <img class="icon-arrow subBtn" src="https://mona.media/template/assets/images/mega-menu-new/mega-menu-next.svg" alt="">
        <!-- Submenu structure omitted for brevity -->
      </div>
      <div class="menu-item menu-item-js"><a class="menu-item-link d-flex detect-link-js menu-mona-custom-link" href="https://mona.media/ban-tin-mona/" data-wpel-link="internal"><span class="icon"><img src="https://mona.media/template/assets/images/header/icon-activity.svg" alt=""></span><span class="txt">Hoạt động</span></a></div>
      <div class="menu-item hop-tac menu-item-js"><a class="menu-item-link d-flex detect-link-js menu-mona-custom-link" href="https://mona.media/hop-tac-lam-an-voi-mona/" data-wpel-link="internal"><span class="icon"><img src="https://mona.media/template/assets/images/header/icon-colleague-02.png" alt=""></span><span class="txt">Hợp tác với MONA</span></a></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MonaTopMenu',
  // Component logic will be added here
};
</script>

<style scoped>
/* Styles based on the mona.media image */
.header-menu {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  background-color: #ffffff; /* White background */
  font-family: Arial, sans-serif; /* A common sans-serif font */
}

.menu-list {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  align-items: center;
}

.menu-item {
  margin-right: 25px; /* Spacing between items */
}

.menu-item-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #333; /* Dark grey text */
  font-size: 14px; /* Approximate font size */
  font-weight: bold; /* Bold text as in image */
  transition: color 0.3s ease;
}

.menu-item-link:hover {
  color: #8A2BE2; /* Purple color on hover (approximated) */
}

.menu-item-link .icon {
  margin-right: 8px; /* Space between icon and text */
  display: flex;
  align-items: center;
}

.menu-item-link .icon img {
  height: 16px; /* Adjust icon size as needed */
  width: auto;
}

.menu-item-link .txt {
  white-space: nowrap;
}

/* Styles for dropdowns - basic structure */
.menu-item.dropdown > .menu-item-link {
  position: relative;
}

.icon-arrow {
  margin-left: 5px;
  height: 10px; /* Adjust as needed */
}

/* Hide elements meant for SP (small screens) by default */
.show-on-sp {
  display: none;
}

/* Placeholder for dropdown/submenu styles */
.mega-menu-wrap,
.submenu {
  display: none; /* Hidden by default, shown on hover/click via JS/CSS */
  position: absolute;
  background-color: #fff;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  z-index: 1000;
  /* More detailed styling would be needed here */
}

.menu-item.dropdown:hover .mega-menu-wrap,
.menu-item.dropdown-sub:hover .submenu {
  display: block; /* Show on hover - basic example */
}

/* Basic styling for sub-menu items */
.submenu-item-link {
  padding: 10px 15px;
  display: block;
  color: #333;
  font-size: 13px;
  text-decoration: none;
}

.submenu-item-link:hover {
  background-color: #f0f0f0;
}
</style> 