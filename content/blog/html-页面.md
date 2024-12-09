---
title: html 页面
date: 2024-12-09T11:13:04.015Z
---

<!DOCTYPE html>
<html lang="zh">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="无敌牛逼的电商页面，超酷设计，惊艳效果，提升用户体验！">
    <title>牛逼电商平台</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: #1a1a1a;
            color: white;
            overflow-x: hidden;
        }

        /* 布局容器 */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* 顶部导航栏 */
        header {
            padding: 20px 0;
            background-color: #111;
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 1000;
        }

        header .logo {
            font-size: 28px;
            font-weight: bold;
            color: #ff4081;
            letter-spacing: 1px;
        }

        header nav {
            display: flex;
            justify-content: flex-end;
            gap: 40px;
        }

        header nav a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            position: relative;
            transition: color 0.3s;
        }

        header nav a:hover {
            color: #ff4081;
        }

        /* 首页展示部分 */
        .hero-section {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: url('https://via.placeholder.com/1500x1000/ff4081/ffffff?text=Shop+With+Us') no-repeat center center/cover;
            position: relative;
        }

        .hero-content {
            text-align: center;
            z-index: 10;
        }

        .hero-content h1 {
            font-size: 56px;
            margin-bottom: 20px;
            text-transform: uppercase;
            color: #fff;
            letter-spacing: 2px;
            animation: fadeIn 2s ease-out;
        }

        .hero-content p {
            font-size: 18px;
            margin-bottom: 30px;
            color: rgba(255, 255, 255, 0.8);
            animation: fadeIn 2s ease-out 0.5s;
        }

        .btn {
            background-color: #ff4081;
            color: #fff;
            padding: 14px 30px;
            text-transform: uppercase;
            font-size: 18px;
            border-radius: 5px;
            text-decoration: none;
            transition: transform 0.3s ease;
        }

        .btn:hover {
            transform: scale(1.1);
        }

        /* 动画效果 */
        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(20px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* 产品展示部分 */
        .products-section {
            padding: 80px 0;
            background-color: #121212;
        }

        .products-section h2 {
            text-align: center;
            font-size: 36px;
            color: #fff;
            margin-bottom: 40px;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 30px;
        }

        .product-item {
            background-color: #2b2b2b;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease;
        }

        .product-item:hover {
            transform: translateY(-10px);
        }

        .product-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .product-info {
            padding: 20px;
            text-align: center;
        }

        .product-info h3 {
            font-size: 22px;
            color: #fff;
            margin-bottom: 15px;
        }

        .product-info p {
            font-size: 16px;
            color: rgba(255, 255, 255, 0.7);
            margin-bottom: 20px;
        }

        .product-info .price {
            font-size: 20px;
            color: #ff4081;
            font-weight: bold;
        }

        /* 底部区域 */
        footer {
            background-color: #111;
            padding: 40px 0;
            text-align: center;
            color: #fff;
        }

        footer a {
            color: #ff4081;
            text-decoration: none;
            font-weight: bold;
        }

        footer a:hover {
            text-decoration: underline;
        }

        /* 响应式 */
        @media (max-width: 768px) {
            .hero-content h1 {
                font-size: 36px;
            }

            .hero-content p {
                font-size: 16px;
            }
        }
    </style>
</head>

<body>

    <!-- 顶部导航栏 -->
    <header>
        <div class="container">
            <div class="logo">牛逼电商</div>
            <nav>
                <a href="#">首页</a>
                <a href="#">产品</a>
                <a href="#">优惠活动</a>
                <a href="#">联系我们</a>
            </nav>
        </div>
    </header>

    <!-- 首页展示 -->
    <section class="hero-section">
        <div class="hero-content">
            <h1>欢迎来到牛逼电商平台</h1>
            <p>全球最牛的购物体验，畅享优质商品，超乎你的想象！</p>
            <a href="#" class="btn">立即购物</a>
        </div>
    </section>

    <!-- 产品展示 -->
    <section class="products-section">
        <div class="container">
            <h2>热门商品</h2>
            <div class="product-grid">
                <div class="product-item">
                    <img src="https://via.placeholder.com/500x300/ff4081/ffffff?text=Product+1" alt="Product 1" class="product-img">
                    <div class="product-info">
                        <h3>产品 1</h3>
                        <p>这是一款非常酷的产品，拥有无敌的性能和设计。</p>
                        <div class="price">¥799</div>
                    </div>
                </div>
                <div class="product-item">
                    <img src="https://via.placeholder.com/500x300/ff4081/ffffff?text=Product+2" alt="Product 2" class="product-img">
                    <div class="product-info">
                        <h3>产品 2</h3>
                        <p>顶级科技，带来不一样的使用体验。</p>
                        <div class="price">¥1299</div>
                    </div>
                </div>
                <div class="product-item">
                    <img src="https://via.placeholder.com/500x300/ff4081/ffffff?text=Product+3" alt="Product 3" class="product-img">
                    <div class="product-info">
                        <h3>产品 3</h3>
                        <p>超高性价比，适合所有人。</p>
                        <div class="price">¥599</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 底部 -->
    <footer>
        <p>&copy; 2024 牛逼电商平台 | <a href="#">隐私政策</a> | <a href="#">服务条款</a></p>
    </footer>

</body>

</html>
