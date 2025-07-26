# Bối cảnh công nghệ

Dự án "Web Giá Rẻ" được xây dựng với các công nghệ chính sau:

*   **Frontend Framework:** Vue 3 (sử dụng Composition API)
*   **Ngôn ngữ:** TypeScript (để đảm bảo tính an toàn kiểu dữ liệu và khả năng mở rộng)
*   **CSS Preprocessor:** Sass/SCSS (để quản lý style một cách hiệu quả hơn với các biến, mixin và lồng ghép)
*   **Build Tool:** Vite (cung cấp trải nghiệm phát triển nhanh chóng với HMR và tối ưu hóa build)

**Cấu trúc dự án:**
*   `src/`: Chứa mã nguồn chính của ứng dụng.
    *   `src/App.vue`: Component gốc của ứng dụng.
    *   `src/main.ts`: Điểm khởi đầu của ứng dụng Vue.
    *   `src/style.css`: File CSS toàn cục (sẽ được chuyển sang SCSS nếu cần).
    *   `src/assets/`: Chứa các tài nguyên tĩnh như hình ảnh, icon, font.
    *   `src/components/`: Chứa các component Vue có thể tái sử dụng.
    *   `src/memory-bank/`: Thư mục chứa các tài liệu Memory Bank.
*   `public/`: Chứa các tài nguyên tĩnh được phục vụ trực tiếp.
*   `package.json`: Quản lý các dependency và script.
*   `tsconfig.json`, `tsconfig.app.json`, `tsconfig.node.json`: Cấu hình TypeScript.
*   `vite.config.ts`: Cấu hình Vite.

**Các lệnh phát triển cơ bản:**
*   `npm install`: Cài đặt các dependency.
*   `npm run dev`: Chạy ứng dụng ở chế độ phát triển.
*   `npm run build`: Build ứng dụng để triển khai.
*   `npm run preview`: Xem trước bản build.

**Quy ước mã hóa:**
*   Sử dụng TypeScript thay vì JavaScript.
*   Sử dụng Sass/SCSS thay vì CSS thuần.
*   Tuân thủ các quy tắc linting và formatting được định nghĩa trong dự án (nếu có).
