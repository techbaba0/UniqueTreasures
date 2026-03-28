<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UniqueTreasures - Rare & One-of-a-Kind Items</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #667eea;
        }

        .cart-btn {
            position: relative;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1rem;
            transition: transform 0.3s;
        }

        .cart-btn:hover {
            transform: scale(1.05);
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #ff4757;
            color: white;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><rect fill="%23667eea" width="1200" height="600"/><circle fill="%23764ba2" opacity="0.3" cx="200" cy="150" r="100"/><circle fill="%23f0932b" opacity="0.4" cx="800" cy="250" r="80"/><circle fill="%23ff4757" opacity="0.3" cx="1000" cy="400" r="120"/></svg>');
            background-size: cover;
            height: 100vh;
            display: flex;
            align-items: center;
            text-align: center;
            color: white;
            margin-top: 80px;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1s ease;
        }

        .hero p {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .cta-btn {
            display: inline-block;
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            color: white;
            padding: 1.2rem 3rem;
            border-radius: 50px;
            text-decoration: none;
            font-size: 1.2rem;
            font-weight: bold;
            transition: transform 0.3s, box-shadow 0.3s;
            animation: fadeInUp 1s ease 0.4s both;
        }

        .cta-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(255, 107, 107, 0.4);
        }

        /* Products Section */
        .products {
            padding: 100px 0;
            background: white;
        }

        .section-title {
            text-align: center;
            font-size: 3rem;
            margin-bottom: 3rem;
            color: #333;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .product-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 60px rgba(0,0,0,0.2);
        }

        .product-image {
            height: 250px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            position: relative;
            overflow: hidden;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .product-card:hover .product-image img {
            transform: scale(1.1);
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.4rem;
            margin-bottom: 0.5rem;
            color: #333;
        }

        .product-price {
            font-size: 1.8rem;
            font-weight: bold;
            color: #ff6b6b;
            margin-bottom: 1rem;
        }

        .product-description {
            color: #666;
            margin-bottom: 1.5rem;
            line-height: 1.5;
        }

        .add-to-cart {
            width: 100%;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 10px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s;
        }

        .add-to-cart:hover {
            background: linear-gradient(45deg, #5a67d8, #6b46c1);
        }

        /* Cart Modal */
        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            backdrop-filter: blur(5px);
        }

        .cart-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            border-radius: 20px;
            max-width: 600px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .cart-header {
            padding: 2rem;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .close-cart {
            background: none;
            border: none;
            font-size: 2rem;
            cursor: pointer;
            color: #999;
        }

        .cart-items {
            padding: 0 2rem 2rem;
        }

        .cart-item {
            display: flex;
            gap: 1rem;
            padding: 1rem 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item img {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: 10px;
        }

        .cart-item-info h4 {
            margin-bottom: 0.5rem;
        }

        .cart-total {
            padding: 0 2rem 2rem;
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #333;
        }

        .checkout-btn {
            width: 100%;
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            color: white;
            border: none;
            padding: 1.5rem;
            border-radius: 0 0 20px 20px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.2rem;
            }

            .products-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Scrollbar */
        .cart-content::-webkit-scrollbar {
            width: 8px;
        }

        .cart-content::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }

        .cart-content::-webkit-scrollbar-thumb {
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <nav class="container">
            <a href="#" class="logo">UniqueTreasures</a>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#products">Shop</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <button class="cart-btn" onclick="toggleCart()">
                <i class="fas fa-shopping-cart"></i>
                <span class="cart-count" id="cartCount">0</span>
            </button>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="container">
            <h1>Discover Unique Treasures</h1>
            <p>One-of-a-kind items you'll never find anywhere else</p>
            <a href="#products" class="cta-btn">Shop Now</a>
        </div>
    </section>

    <!-- Products Section -->
    <section class="products" id="products">
        <div class="container">
            <h2 class="section-title">Featured Collections</h2>
            <div class="products-grid">
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://images.unsplash.com/photo-1581686995891-8c6c1d43b10e?w=400&h=250&fit=crop" alt="Vintage Pocket Watch">
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Victorian Pocket Watch</h3>
                        <div class="product-price">$299</div>
                        <p class="product-description">Authentic 1890s Swiss pocket watch with original enamel dial and gold case.</p>
                        <button class="add-to-cart" onclick="addToCart('Victorian Pocket Watch', 299, 'https://images.unsplash.com/photo-1581686995891-8c6c1d43b10e?w=80&h=80&fit=crop')">
                            Add to Cart
                        </button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">
                        <img src="https://images.unsplash.com/photo-1586023492125-27b2c045efd7?w=400&h=250&fit=crop" alt="Handmade Ceramic Vase">
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Raku Ceramic Vase</h3>
                        <div class="product-price">$189</div>
                        <p class="product-description">Handcrafted Japanese raku vase with unique crackle glaze and iridescent finish.</p>
                        <button class="add-to-cart" onclick="addToCart('Raku Ceramic Vase', 189, 'https://images.unsplash.com/photo-1586023492125-27b2c045efd7?w=80&h=80&fit=crop')">
                            Add to Cart
                        </button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">
                        <img src="https://images.unsplash.com/photo-1544968045-8f7ea10c8b96?w=400&h=250&fit=crop" alt="Ancient Coin">
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Roman Silver Denarius</h3>
                        <div class="product-price">$1,250</div>
                        <p class="product-description">Rare silver denarius from Emperor Trajan (98-117 AD) with excellent detail preservation.</p>
                        <button class="add-to-cart" onclick="addToCart('Roman Silver Denarius', 1250, 'https://images.unsplash.com/photo-1544968045-8f7ea10c8b96?w=80&h=80&fit=crop')">
                            Add to Cart
                        </button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">
                        <img src="https://images.unsplash.com/photo-1578864208458-8d0e3e5fc2a2?w=400&h=250&fit=crop" alt="Vintage Typewriter">
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Underwood Typewriter</h3>
                        <div class="product-price">$450</div>
                        <p class="product-description">Restored 1930s Underwood No. 5 typewriter in mint working condition with original case.</p>
                        <button class="add-to-cart" onclick="addToCart('Underwood Typewriter', 450, 'https://images.unsplash.com/photo-1578864208458-8d0e3e5fc2a2?w=80&h=80&fit=crop')">
                            Add to Cart
                        </button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">
                        <img src="https://images.unsplash.com/photo-1605348532760-6753d2c43329?w=400&h=250&fit=crop" alt="Hand-carved Box">
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Ebony Jewelry Box</h3>
                        <div class="product-price">$325</div>
                        <p class="product-description">Hand-carved ebony wood box with mother-of-pearl inlay and secret compartment.</p>
                        <button class="add-to-cart" onclick="addToCart('Ebony Jewelry Box', 325, 'https://images.unsplash.com/photo-1605348532760-6753d2c43329?w=80&h=80&fit=crop')">
                            Add to Cart
                        </button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">
                        <img src="https://images.unsplash.com/photo-1581235720704-06d1018152f5?w=400&h=250&fit=crop" alt="Meteorite Specimen">
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Iron Meteorite</h3>
                        <div class="product-price">$899</div>
                        <p class="product-description">1.2kg authenticated iron meteorite slice with stunning Widmanstätten pattern.</p>
                        <button class="add-to-cart" onclick="addToCart('Iron Meteorite', 899, 'https://images.unsplash.com/photo-1581235720704-06d1018152f5?w=80&h=80&fit=crop')">
                            Add to Cart
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Cart Modal -->
    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <div class="cart-header">
                <h2>Your Cart</h2>
                <button class="close-cart" onclick="toggleCart()">&times;</button>
            </div>
            <div class="cart-items" id="cartItems">
                <p style="text-align: center; padding: 2rem; color: #666;">Your cart is empty</p>
            </div>
            <div class="cart-total" id="cartTotal">$0.00</div>
            <button class="checkout-btn" onclick="checkout()">Proceed to Checkout</button>
        </div>
    </
