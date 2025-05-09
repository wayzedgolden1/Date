---sanpham.css---
.card-img-top {
    height: 200px;
    object-fit: cover;
}
body {
    background-color: #a5b2fc;
}

.khung {
    background-color: #ffffff;     /* Nền trắng hoặc màu bạn thích */
    padding: 30px;
    margin: 40px auto;
    border-radius: 15px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    max-width: 8000px;
    color: #333;
}

.card {
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
    transform: scale(1.02);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
}

.form-control:focus {
    border-color: #0d6efd;
    box-shadow: 0 0 0 0.2rem rgba(13, 110, 253, 0.25);
}

header h1 {
    font-weight: bold;
}

.btn-warning,
.btn-danger {
    margin-right: 5px;
}
/* Giao diện chung */
body {
    transition: background-color 0.3s ease, color 0.3s ease;
}

.card {
    transition: background-color 0.3s ease, color 0.3s ease;
}

.form-control, .btn {
    transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease;
}

/* Dark mode */
.dark-mode {
    background-color: #121212;
    color: #e0e0e0;
}

.dark-mode .card {
    background-color: #1e1e1e;
    border-color: #333;
    color: #e0e0e0;
}

.dark-mode .form-control {
    background-color: #2c2c2c;
    border-color: #555;
    color: #fff;
}

.dark-mode .form-control::placeholder {
    color: #aaa;
}

.dark-mode .btn-outline-primary {
    color: #ccc;
    border-color: #888;
}

.dark-mode .btn-outline-primary:hover {
    background-color: #333;
    color: #fff;
}

.dark-mode header,
.dark-mode footer {
    background-color: #1f1f1f !important;
    color: #e0e0e0;
}

.dark-mode .btn-outline-light {
    border-color: #ccc;
    color: #fff;
}
/* CSS cho chế độ tối */
body.dark-mode {
    background-color: #121212;
    color: #fff;
}

/* Hiệu ứng fade-in cho các phần tử */
.fade-in {
    animation: fadeIn 1s ease-out;
}

/* Hiệu ứng slide-in từ trái cho header */
@keyframes slideIn {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

.slide-in-left {
    animation: slideIn 1s ease-out;
}

/* Hiệu ứng hover cho nút */
button:hover {
    transform: scale(1.1);
    transition: transform 0.3s ease;
}

/* Hiệu ứng fade-in cho các phần tử khi người dùng cuộn xuống */
.fade-in-on-scroll {
    opacity: 0;
    animation: fadeInOnScroll 1s forwards;
}

@keyframes fadeInOnScroll {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

/* Hiệu ứng ẩn/hiện footer */
.footer-slide-in {
    animation: footerSlideIn 1s ease-in-out;
}

@keyframes footerSlideIn {
    from {
        transform: translateY(100%);
    }
    to {
        transform: translateY(0);
    }
}
/* CSS cho chế độ tối */
body.dark-mode {
    background-color: #121212; /* Nền tối */
    color: #f5f5f5; /* Màu chữ sáng */
}

body.dark-mode .form-control,
body.dark-mode .btn,
body.dark-mode .form-select {
    background-color: #333; /* Nền tối cho các ô input và nút */
    color: #f5f5f5; /* Màu chữ sáng */
    border: 1px solid #555; /* Viền cho các ô input */
}

body.dark-mode .card,
body.dark-mode .footer-slide-in {
    background-color: #222; /* Nền tối cho các card và footer */
    color: #f5f5f5; /* Màu chữ sáng */
}

body.dark-mode a {
    color: #99ccff; /* Màu chữ của liên kết trong chế độ tối */
}

body.dark-mode a:hover {
    color: #ffffff; /* Màu chữ khi hover */
}
/* Đảm bảo trang chiếm toàn bộ chiều cao */
body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    margin: 0;
}

/* Đẩy phần nội dung chính lên để footer luôn nằm dưới */
.container {
    flex: 1;
}
@keyframes rotate-scale {
    0% { transform: scale(1) rotate(0deg); }
    50% { transform: scale(1.1) rotate(5deg); }
    100% { transform: scale(1) rotate(0deg); }
  }
  
  .logo-animated {
    animation: rotate-scale 1.5s ease-in-out infinite;
  }
  /* Đảm bảo icon sáng/tối được hiển thị chính xác */
.sun-icon {
    content: '🌞'; /* Chế độ sáng */
}
