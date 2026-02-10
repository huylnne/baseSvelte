# Svelte Hello World - 3D Viewer Container

Đây là một ứng dụng demo Svelte + Vite, chuẩn bị để tích hợp 3D viewer (HOOPS/WebGL) sau này.

## Cấu trúc Project

```
svelte-hello/
├── src/
│   ├── main.js              # Entry point của ứng dụng
│   ├── App.svelte           # Component chính
│   ├── app.css              # Global styles
│   ├── components/
│   │   ├── Header.svelte    # Header component
│   │   └── ViewerContainer.svelte  # Container cho 3D viewer
│   └── lib/
│       └── Counter.svelte   # Counter component mẫu
├── public/                  # Static assets
├── index.html              # HTML template
├── vite.config.js          # Vite configuration
├── svelte.config.js        # Svelte configuration
└── package.json            # Dependencies
```

## Yêu cầu hệ thống

- Node.js 16+ 
- npm hoặc yarn

## Cài đặt

1. Clone hoặc tải project về máy

2. Cài đặt dependencies:
```bash
npm install
```

## Chạy ứng dụng

### Chế độ Development
```bash
npm run dev
```
Ứng dụng sẽ chạy tại `http://localhost:5173` (hoặc port khác nếu 5173 đã được sử dụng)

### Build cho Production
```bash
npm run build
```
Tạo build tối ưu trong thư mục `dist/`

### Preview bản build
```bash
npm run preview
```
Xem trước bản build production tại local

## Các Component chính

### App.svelte
Component gốc của ứng dụng, chứa layout chính với [`Header`](src/components/Header.svelte) và [`ViewerContainer`](src/components/ViewerContainer.svelte).

### Header.svelte
Hiển thị tiêu đề và mô tả ứng dụng.

### ViewerContainer.svelte
Container dành cho việc tích hợp 3D viewer trong tương lai. Component này:
- Sử dụng `onMount` để khởi tạo viewer khi component được mount
- Có sẵn cleanup logic trong `onDestroy`
- Hiện tại hiển thị placeholder với kích thước 520px height

## Tích hợp 3D Viewer (Kế hoạch)

Để tích hợp HOOPS hoặc WebGL viewer, chỉnh sửa [`ViewerContainer.svelte`](src/components/ViewerContainer.svelte):

```javascript
onMount(() => {
  // Uncomment và implement các function này
  initViewer(viewerEl);

  return () => {
    destroyViewer();
  };
});
```

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte for VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)

## Tính năng kỹ thuật

### Svelte 5
Project sử dụng Svelte 5 với cú pháp mới:
- `$state` runes cho reactive state (xem [`Counter.svelte`](src/lib/Counter.svelte))
- `onMount` và `onDestroy` lifecycle hooks

### Vite
- Hot Module Replacement (HMR)
- Fast development server
- Optimized production builds

### Styling
- Global styles trong [`app.css`](src/app.css)
- Component-scoped styles
- Dark/Light mode support

## Cấu hình

### jsconfig.json
Đã cấu hình:
- `checkJs: true` - Type checking cho JavaScript
- `moduleResolution: "bundler"`
- Support cho Svelte files

### vite.config.js
Cấu hình cơ bản với Svelte plugin, có thể mở rộng thêm:
```javascript
// Thêm alias, proxy, v.v...
```

## HMR và State Management

⚠️ **Lưu ý**: HMR không preserve local component state mặc định.

Nếu cần giữ state quan trọng, tạo external store:

```javascript
// src/stores/viewer.js
import { writable } from 'svelte/store'
export const viewerState = writable({
  isLoaded: false,
  model: null
})
```

Chi tiết: [svelte-hmr documentation](https://github.com/sveltejs/svelte-hmr/tree/master/packages/svelte-hmr#preservation-of-local-state)

## Troubleshooting

### Port đã được sử dụng
Vite sẽ tự động chọn port khác. Hoặc chỉ định port cụ thể trong [`vite.config.js`](vite.config.js):
```javascript
export default defineConfig({
  plugins: [svelte()],
  server: {
    port: 3000
  }
})
```

### Module not found
Chạy lại:
```bash
npm install
```

## Nâng cấp lên SvelteKit

Nếu cần routing và SSR, có thể migrate sang [SvelteKit](https://kit.svelte.dev/). Project structure đã tương thích để dễ migration.

## License

MIT

## Liên hệ

Để biết thêm chi tiết về Svelte, xem [Svelte documentation](https://svelte.dev/docs).