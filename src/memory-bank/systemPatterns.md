# Các mẫu hệ thống

Dự án "Web Giá Rẻ" tuân theo kiến trúc dựa trên component của Vue 3, cho phép phát triển module và khả năng tái sử dụng cao.

**Kiến trúc tổng quan:**
*   **Component-based Architecture:** Ứng dụng được xây dựng từ các component nhỏ, độc lập và có thể tái sử dụng.
*   **Single File Components (SFCs):** Mỗi component Vue được định nghĩa trong một tệp `.vue` duy nhất, bao gồm template (HTML), script (TypeScript) và style (Sass/SCSS).
*   **Composition API:** Sử dụng Composition API của Vue 3 để tổ chức logic component một cách linh hoạt và dễ bảo trì hơn, đặc biệt với các component phức tạp.

**Cấu trúc thư mục `src/components/`:**
*   Các component được tổ chức theo chức năng hoặc theo trang mà chúng thuộc về.
*   Ví dụ:
    *   `SimplePageHero.vue`: Component hero section cho trang Simple Page.
    *   `MauWebsiteHero.vue`: Component hero section cho trang Mẫu Website.
    *   `MobioSection.vue`, `CanhcamServicesSection.vue`, `DemoStackingCards.vue`: Các section cụ thể được sử dụng trên các trang khác nhau.
    *   `MonaTopMenu.vue`, `ThuyThuTopMenu.vue`: Các component menu điều hướng.
    *   `ContactSection.vue`, `FooterSection.vue`: Các component chung cho các phần liên hệ và chân trang.

**Quản lý dữ liệu:**
*   Dữ liệu cho các trang và component có thể được định nghĩa trong các tệp JSON riêng biệt (ví dụ: `simplepage.json`, `mauwebsite.json`, `monamedia.json`, `tamnguyen.json`, `thuythu.json`, `elementor.json`).
*   Các component sẽ đọc và hiển thị dữ liệu từ các tệp JSON này, cho phép dễ dàng cập nhật nội dung mà không cần thay đổi mã nguồn component.

**Quy ước đặt tên:**
*   Component Vue: Sử dụng PascalCase (ví dụ: `SimplePageHero.vue`).
*   Tệp SCSS: Sử dụng kebab-case (ví dụ: `_variables.scss`, `_mixins.scss`).

**Tích hợp và tái sử dụng:**
*   Các component được thiết kế để có thể dễ dàng import và sử dụng trong các trang hoặc component khác.
*   Mục tiêu là tối đa hóa khả năng tái sử dụng code để giảm thời gian phát triển và duy trì tính nhất quán.
