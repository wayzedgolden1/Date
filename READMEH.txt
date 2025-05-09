---sanpham.html---
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title data-i18n="title">Radiant Trio Store</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Custom CSS -->
    <link rel="stylesheet" href="../css/sanpham.css">
</head>
<body>
    <!-- Header -->
    <header class="text-white py-4 mb-4 shadow d-flex justify-content-between align-items-center px-4 slide-in-left position-relative"
        style="background-image: url('../img/2.jpg'); background-size: cover; background-position: center;">
        <div class="d-flex align-items-center gap-3">
            <img src="../img/1.png" alt="Logo" style="height: 40px;" class="logo-animated">
        </div>
        <div class="d-flex align-items-center gap-2">
            <a href="giohang.html" class="btn btn-outline-light position-relative">
                🛒
                <span class="visually-hidden">Giỏ hàng</span>
            </a>
            <select id="languageSelect" class="form-select form-select-sm">
                <option value="vi">VI</option>
                <option value="en">EN</option>
            </select>
            <button id="toggleDarkMode" class="btn btn-outline-light">
                ☀️ <span class="d-none"></span>
            </button>
            <button id="logoutBtn" class="btn btn-danger">Đăng xuất</button>
        </div>
    </header>

    <div class="container mb-5">
        <!-- Form thêm/sửa sản phẩm -->
        <div class="card shadow-sm mb-4 fade-in">
            <div class="card-body">
                <form id="productForm" class="row g-3">
                    <input type="hidden" id="productId">
                    <div class="col-md-3">
                        <input type="text" class="form-control" id="ten" placeholder="Tên sản phẩm" required data-i18n-placeholder="name">
                    </div>
                    <div class="col-md-3">
                        <input type="text" class="form-control" id="mota" placeholder="Mô tả" required data-i18n-placeholder="description">
                    </div>
                    <div class="col-md-2">
                        <input type="number" class="form-control" id="gia" placeholder="Giá" required data-i18n-placeholder="price">
                    </div>
                    <div class="col-md-3">
                        <input type="text" class="form-control" id="hinhanh" placeholder="URL hình ảnh" required data-i18n-placeholder="image_url">
                    </div>
                    <div class="col-md-1 d-grid">
                        <button type="submit" class="btn btn-success" data-i18n="save">Lưu</button>
                    </div>
                </form>
            </div>
        </div>

        <!-- Form tìm kiếm và lọc -->
        <div class="card shadow-sm mb-4 fade-in">
            <div class="card-body">
                <div class="row g-3">
                    <div class="col-md-4">
                        <input type="text" id="searchInput" class="form-control" placeholder="Tìm theo tên sản phẩm..." data-i18n-placeholder="search_name">
                    </div>
                    <div class="col-md-3">
                        <input type="number" id="minPrice" class="form-control" placeholder="Giá thấp nhất" data-i18n-placeholder="min_price">
                    </div>
                    <div class="col-md-3">
                        <input type="number" id="maxPrice" class="form-control" placeholder="Giá cao nhất" data-i18n-placeholder="max_price">
                    </div>
                    <div class="col-md-2 d-grid">
                        <button type="button" class="btn btn-outline-primary" onclick="applyFilters(event)" data-i18n="filter">Lọc</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Danh sách sản phẩm -->
        <div class="row row-cols-1 row-cols-md-3 g-4" id="productList"></div>
    </div>

    <!-- Footer -->
    <footer class="bg-white text-center text-muted py-3 border-top footer-slide-in">
        <span data-i18n="footer">&copy; 2025 Phát triển bởi Radiant Trio</span>
    </footer>

    <!-- Modal chọn số lượng -->
    <div class="modal fade" id="quantityModal" tabindex="-1" aria-labelledby="quantityModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="quantityModalLabel">Chọn số lượng</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Đóng"></button>
                </div>
                <div class="modal-body">
                    <input type="number" id="quantityInput" class="form-control" min="1" value="1">
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Hủy</button>
                    <button type="button" class="btn btn-primary" id="saveQuantityButton">Đồng ý</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Scripts -->
    <script src="../js/sanpham.js"></script>
    <script>
        const body = document.body;
        const translations = {
            vi: {
                title: "Radiant Trio Store",
                header: "Quản Lý Sản Phẩm",
                dark_mode: "Chế độ tối",
                light_mode: "Chế độ sáng",
                name: "Tên sản phẩm",
                description: "Mô tả",
                price: "Giá",
                image_url: "URL hình ảnh",
                save: "Lưu",
                search_name: "Tìm theo tên sản phẩm...",
                min_price: "Giá thấp nhất",
                max_price: "Giá cao nhất",
                filter: "Lọc",
                footer: "© 2025 Phát triển bởi Radiant Trio"
            },
            en: {
                title: "Radiant Trio Store",
                header: "Product Management",
                dark_mode: "Dark Mode",
                light_mode: "Light Mode",
                name: "Product Name",
                description: "Description",
                price: "Price",
                image_url: "Image URL",
                save: "Save",
                search_name: "Search by product name...",
                min_price: "Min Price",
                max_price: "Max Price",
                filter: "Filter",
                footer: "© 2025 Developed by Radiant Trio"
            }
        };

        let currentLang = localStorage.getItem("lang") || "vi";
        document.getElementById("languageSelect").value = currentLang;

        function updateLanguage(lang) {
            currentLang = lang;
            localStorage.setItem("lang", lang);

            document.querySelectorAll("[data-i18n]").forEach(el => {
                const key = el.getAttribute("data-i18n");
                if (translations[lang][key]) el.textContent = translations[lang][key];
            });

            document.querySelectorAll("[data-i18n-placeholder]").forEach(el => {
                const key = el.getAttribute("data-i18n-placeholder");
                if (translations[lang][key]) el.placeholder = translations[lang][key];
            });

            toggleBtn.querySelector("span").textContent = body.classList.contains("dark-mode")
                ? translations[lang]["light_mode"]
                : translations[lang]["dark_mode"];
        }

        const toggleBtn = document.getElementById("toggleDarkMode");

        if (localStorage.getItem("darkMode") === "true") {
        body.classList.add("dark-mode");
        toggleBtn.querySelector("span").textContent = translations[currentLang]["light_mode"];
        }

        toggleBtn.addEventListener("click", () => {
        body.classList.toggle("dark-mode");
        const isDark = body.classList.contains("dark-mode");
        localStorage.setItem("darkMode", isDark);
        toggleBtn.innerHTML = isDark
            ? '🌙 <span class="d-none">Chế độ tối</span>'
            : '☀️ <span class="d-none">Chế độ sáng</span>';
        });

        document.getElementById("languageSelect").addEventListener("change", (e) => {
            updateLanguage(e.target.value);
        });

        updateLanguage(currentLang);

        // Xử lý nút đăng xuất
        document.getElementById("logoutBtn").addEventListener("click", () => {
            localStorage.removeItem("user"); // hoặc token, v.v...
            alert(currentLang === "vi" ? "Bạn đã đăng xuất." : "You have logged out.");
            window.location.href = "dangnhap.html";
        });

         

        // Xử lý thêm giỏ hàng
        let selectedProductForCart = null;

        document.addEventListener("click", function (e) {
            if (e.target.classList.contains("add-to-cart-btn")) {
                const productCard = e.target.closest(".product-card");
                selectedProductForCart = {
                    id: e.target.dataset.id,
                    ten: productCard.querySelector(".product-name").textContent,
                    mota: productCard.querySelector(".product-description").textContent,
                    gia: parseInt(productCard.querySelector(".product-price").dataset.price),
                    hinhanh: productCard.querySelector("img").src
                };
                const modal = new bootstrap.Modal(document.getElementById("quantityModal"));
                modal.show();
            }
        });

        document.getElementById("saveQuantityButton").addEventListener("click", () => {
            const quantity = parseInt(document.getElementById("quantityInput").value) || 1;
            if (!selectedProductForCart) return;
            selectedProductForCart.soluong = quantity;

            let cart = JSON.parse(localStorage.getItem("cart")) || [];
            const existing = cart.find(item => item.id == selectedProductForCart.id);
            if (existing) {
                existing.soluong += quantity;
            } else {
                cart.push(selectedProductForCart);
            }
            localStorage.setItem("cart", JSON.stringify(cart));

            const modal = bootstrap.Modal.getInstance(document.getElementById("quantityModal"));
            modal.hide();
            alert("Đã thêm vào giỏ hàng với số lượng: " + quantity);
        });
    </script>

    <!-- Bootstrap JS -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
