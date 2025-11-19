<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nike Store</title>
    <style>
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: #333;
        }

     
        header {
            background-color: #111;
            color: #fff;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            font-size: 24px;
            color: #ff4a1c;
            cursor: pointer;
        }

        nav a {
            color: #fff;
            text-decoration: none;
            margin: 0 15px;
        }

        nav a:hover {
            color: #ff4a1c;
        }


        /* Main Section */
        .main {
            padding: 40px 20px;
            text-align: center;
        }

        .main h2 {
            font-size: 36px;
            margin-bottom: 20px;
            color: #333;
        }

        .video-section video {
            width: 100%;
            height: auto;
        }

        .video-section p {
            font-size: 18px;
            color: #333;
            margin-top: 10px;
            font-weight: bold;
        }

        .product {
            display: inline-block;
            width: 250px;
            margin: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s;
        }
        
        .product:hover {
            transform: scale(1.05);
        }

        .product img {
            width: 100%;
            height: auto;
            border-radius: 10px;
        }

        .product h3 {
            font-size: 18px;
            margin: 10px 0;
            color: #333;
        }

        .product p {
            color: #777;
            margin: 10px 0;
        }

        .product button {
            background-color: #ff4a1c;
            border: none;
            padding: 10px 20px;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }

        .product button:hover {
            background-color: #e03a14;
        }
        .product-header {
    text-align: left;
    margin-left: 20px;
    font-size: 24px;
    color: #333;
    position: relative; 
}

        
       
        .promo-section {
            margin-top: 20px;
            text-align: center;
        }

        .promo-section h2 {
            font-size: 32px;
            font-weight: bold;
            color: #333;
        }

        .promo-section p {
            font-size: 16px;
            margin: 10px 0;
        }

        .promo-section button {
            background-color: #111;
            color: #fff;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .promo-section button:hover {
            background-color: #333;
        }
        #products {
    overflow-x: auto;
    white-space: nowrap;
    padding: 20px;
    scrollbar-width: none; 
}
.user-menu {
    position: relative;
    display: inline-block;
}

.dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    z-index: 1;
}

.dropdown-content a {
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
}
.dropdown-content a.disabled {
    color: #ccc; 
    pointer-events: none; 
}

.dropdown-content a:hover {
    background-color: #f1f1f1;
}

.user-menu:hover .dropdown-content {
    display: block;
}
#products::-webkit-scrollbar {
    display: none; 
}

 .cart {
            margin-top: 40px;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
        }

        .cart h2 {
            margin-bottom: 20px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }

        .cart-item span {
            margin-right: 10px;
        }
        /* Footer */
        footer {
            
            background-color: #111;
            color: #fff;
            padding: 20px;
            text-align: center;
            margin-top: 40px;
        }
    </style>
</head>
<body>
    

    <!-- Header -->
    <body>
        <!-- Header -->
        <header>
            <h1>Nike</h1>
            <nav>
                <a onclick="window.location.href='https://www.google.com/maps/search/nike+store/@12.7720272,77.4702736,11z/data=!3m1!4b1?entry=ttu&g_ep=EgoyMDI0MTIwNC4wIKXMDSoASAFQAw%3D%3D'" href="#home">Find a store</a>
                <a href="#products">Products</a>
                <a href="#contact">Contact</a>
                <div class="user-menu">
                    <a id="user-link" href="javascript:void(0)">Sign In</a>
                    <div class="dropdown-content" id="dropdown-content">
                        <a href="profile.html" id="profile-link">Profile</a>
                        <a href="javascript:void(0);" id="cart-link" onclick="window.location.href='checkout.html'">Cart</a>
                        <a href="javascript:void(0);" id="logout-link" onclick="logout()">Log Out</a>
                    </div>
                </div>
            </nav>
        </header>
    
        <script>
            // Check if the user is signed in
            const username = localStorage.getItem('username');
            const userLink = document.getElementById('user-link');
    
            if (username) {
                userLink.textContent = username; 
                userLink.style.pointerEvents = 'none'; 
                userLink.style.color = '#fff'; 
            }
    
            function logout() {
                localStorage.removeItem('username');
                window.location.href = 'sign-in.html'; 
            }
    
            function addToCart(model, size, price, image) {
                const cart = JSON.parse(localStorage.getItem('cart')) || [];
                const item = { model, size, price, quantity: 1, image };
                cart.push(item);
                localStorage.setItem('cart', JSON.stringify(cart));
                alert(${model} added to cart!);
            }
        </script>
    
        
    </body>

    
    <!-- Main Content -->
    <div class="main" id="home">
        <h2>Welcome to Nike Store</h2>
        <p>Explore our latest collection of shoes and sportswear.</p><br>
       
        <div class="video-section">
            <video autoplay muted loop width="100%">
                <source src="videoplayback.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
            <p style="margin-top: 10px;">Discover the latest Nike gear in action!</p>
        </div>

        <div class="promo-section">
            <h2 href="">LET YOUR FIRE RUN.</h2>
            <p>The pain’s real. So is the reward. Push past the breaking point and turn your burning passion into speed with the Ekiden Pack.</p>
            <button onclick="window.location.href='https://play.google.com/store/search?q=nike%20store&c=apps&hl=en'">Shop In App</button>
        </div>
<br>

        <!-- Product Section -->
       
        
      
<div id="products" style="overflow-x: auto; white-space: nowrap; padding: 20px;">
    <div id="products">
        <div class="product-header">TRENDING</div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="NIKE+AIR+MAX+1.png" alt="Nike Air Max">
        <h3>Nike Air Max</h3>
        <p>$120.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes1">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max', 'sizes1', 120.00, 'NIKE+AIR+MAX+1.png')">Add to Cart</button>
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="W+NIKE+REVOLUTION+6+NN.png" alt="Nike Revolution">
        <h3>Nike Revolution</h3>
        <p>$90.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes2">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Revolution', 'sizes2', 90.00, 'W+NIKE+REVOLUTION+6+NN.png')">Add to Cart</button>
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="nike-zoom-fly-featuring-the-zoom-fly-3.jpg" alt="Nike Zoom Fly">
        <h3>Nike Zoom Fly</h3>
        <p>$150.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes4">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Zoom Fly', 'sizes4', 150.00, 'nike-zoom-fly-featuring-the-zoom-fly-3.jpg')">Add to Cart</button>
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="nike air force1.jpg" alt="Nike Air Force 1">
        <h3>Nike Air Force 1</h3>
        <p>$150.00</p>
        <label for="sizes">Select Size:</label>
            <select id="sizes5">
                <option value="7">7</option>
                <option value="8">8</option>
                <option value="9">9</option>
                <option value="10">10</option>
            </select><br><br>
            <button onclick="addToCart('Nike Air Force 1', 'sizes5', 150.00, 'nike air force1.jpg')">Add to Cart</button>
    </div>
    <div class="product" style="display: inline-block;">
        <img src="NIKE+COURT+ROYALE+2+NN.png" alt="Nike Court Royale">
        <h3>Nike Court Royale</h3>
        <p>$110.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes6">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Court Royale', 'sizes6', 110.00, 'NIKE+COURT+ROYALE+2+NN.png')">Add to Cart</button>
    </div>
     <div class="product" style="display: inline-block;">
        <img src="NIKE+AIR+MAX+SC+LEA.png" alt="Nike Air Max SC">
        <h3>Nike Air Max SC</h3>
        <p>$160.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes7">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max SC', 'sizes7', 160.00, 'NIKE+AIR+MAX+SC+LEA.png')">Add to Cart</button>
    </div>
    <div class="product" style="display: inline-block;">
        <img src="NIKE+COURT+VISION+LO+NN.jpg" alt="Nike Court Vision Low">
        <h3>Nike Court Vision Low</h3>
        <p>$140.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes3">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Court Vision Low', 'sizes3', 140.00, 'NIKE+COURT+VISION+LO+NN.jpg')">Add to Cart</button>
    </div>
</div>
<br>



<!--MENNNNN-->
<div id="products" style="overflow-x: auto; white-space: nowrap; padding: 20px;">
    <div id="products">
        <div class="product-header">MEN</div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        
        <img src="kobe-9-elite-high-protro-bright-crimson-and-emerald-green-fz7335-600-release-date.jpg" alt="Kobe IX Elite High Protro">
        <h3>Kobe IX Elite High Protro</h3>
        <p>$250.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes11">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Kobe IX Elite High Protro', 'sizes11', 250.00, 'kobe-9-elite-high-protro-bright-crimson-and-emerald-green-fz7335-600-release-date.jpg')">Add to Cart</button>
    </div>

    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="AIR+ZOOM+PEGASUS+41+SP.png" alt="Nike Air Zoom Pegasus 41 SP">
        <h3>Nike Zoom Pegasus 41 </h3>
        <p>$160.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes12">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Zoom Pegasus 41 SP', 'sizes12', 160.00, 'AIR+ZOOM+PEGASUS+41+SP.png')">Add to Cart</button>
    </div>



    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="NIKE+P-6000.png" alt="Nike P-6000">
        <h3>Nike P-6000</h3>
        <p>$160.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes13">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max', 'sizes13', 160.00, 'NIKE+P-6000.png')">Add to Cart</button>
    </div>
    <div class="product" style="display: inline-block;">
        <img src="JORDAN+STADIUM+90.png" alt="Nike Stadium 90">
        <h3>Nike Stadium 90</h3>
        <p>$160.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes14">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Stadium 90', 'sizes14', 160.00, 'JORDAN+STADIUM+90.png')">Add to Cart</button>
    </div>
     <div class="product" style="display: inline-block;">
        <img src="AIR+JORDAN+1+MID.jpg" alt="Air Jordan Mid 1">
        <h3>Air Jordan Mid 1</h3>
        <p>$150.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes15">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Air Jordan Mid 1', 'sizes15', 150.00, 'AIR+JORDAN+1+MID.jpg')">Add to Cart</button>
        
    </div>

    <div class="product" style="display: inline-block;">
        <img src="AIR+MAX+DN+(GS).png" alt="ANike Air Max Dn SE">
        <h3>Nike Air Max Dn SE</h3>
        <p>$180.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes16">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max Dn SE', 'sizes16', 180.00, 'AIR+MAX+DN+(GS).png')">Add to Cart</button>
        
    </div>

    <div class="product" style="display: inline-block;">
        <img src="NIKE+INITIATOR.png" alt="Nike Initiator">
        <h3>Nike Initiator</h3>
        <p>$140.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes17">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Initiator', 'sizes17', 140.00, 'NIKE+INITIATOR.png')">Add to Cart</button>
        
    </div>
   
</div>
<br>

<!--womenNNNNN-->
<div id="products" style="overflow-x: auto; white-space: nowrap; padding: 20px;">
    <div id="products">
        <div class="product-header">WOMEN</div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="W+NIKE+DUNK+LOW+PRM.png" alt="Nike Dunk Low">
        <h3>Nike Dunk Low</h3>
        <p>$160.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes21">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Dunk Low', 'sizes21', 160.00, 'W+NIKE+DUNK+LOW+PRM.png')">Add to Cart</button>
      
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="NIKE+FLYKNIT+HAVEN.jpg" alt="Nike Flyknit Haven">
        <h3>Nike Flyknit Haven</h3>
        <p>$140.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes22">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Flyknit Haven', 'sizes22', 140.00, 'NIKE+FLYKNIT+HAVEN.jpg')">Add to Cart</button>
       
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="W+AF1+SHADOW.png" alt="Nike Air Force Shadow">
        <h3>Nike Air Force Shadow</h3>
        <p>$150.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes23">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Force Shadow', 'sizes23', 150.00, 'W+AF1+SHADOW.png')">Add to Cart</button>
       
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="NIKE+SB+VERTEBRAE.png" alt="Nike SB Vertebrae">
        <h3>Nike SB Vertebrae</h3>
        <p>$150.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes24">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike SB Vertebrae', 'sizes24', 150.00, 'NIKE+SB+VERTEBRAE.png')">Add to Cart</button>
        
    </div>
    <div class="product" style="display: inline-block;">
        <img src="NIKE+LUNAR+ROAM+SE.png" alt="Nike Lunar Roam">
        <h3>Nike Lunar Roam</h3>
        <p>$150.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes25">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Lunar Roam', 'sizes25', 120.00, 'NIKE+LUNAR+ROAM+SE.png')">Add to Cart</button>
       
    </div>
     <div class="product" style="display: inline-block;">
        <img src="NIKE+AIR+WINFLO+11.png" alt="Nike Winflow 11">
        <h3>Nike Winflow 11</h3>
        <p>$110.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes26">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Winflow 11', 'sizes26', 110.00, 'NIKE+AIR+WINFLO+11.png')">Add to Cart</button>
       
    </div>
    <div class="product" style="display: inline-block;">
        <img src="NIKE+DUNK+LOW+QS.png" alt="Nike Dunk Low 1">
        <h3>Nike Dunk Low 1</h3>
        <p>$145.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizes27">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Dunk Low 1', 'sizes27', 145.00, 'NIKE+DUNK+LOW+QS.png')">Add to Cart</button>
       
    </div>
 
</div>
<!--cLASSICSSS-->
<div id="products" style="overflow-x: auto; white-space: nowrap; padding: 20px;">
    <br>
    
<div id="products" style="overflow-x: auto; white-space: nowrap; padding: 20px;">
    <div id="products">
        <div class="product-header">CLASSICS</div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="AIR+FORCE+1+07+LX.png" alt="Nike Air Force 1'07">
        <h3>Nike Air Force 1'07</h3>
        <p>$180.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesh">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Force 1-07', 'sizesh', 180.00, 'AIR+FORCE+1+07+LX.png')">Add to Cart</button>
        
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="NIKE+AIR+MAX+97.png" alt="Nike Air Max 97">
        <h3>Nike Air Max 97</h3>
        <p>$170.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesg">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max 97', 'sizesg', 170.00, 'NIKE+AIR+MAX+97.png')">Add to Cart</button>
        
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="NIKE+AIR+MAX+AP.png" alt="Nike Air Max AP">
        <h3>Nike Air Max AP</h3>
        <p>$145.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesf">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max AP', 'sizesf', 145.00, 'NIKE+AIR+MAX+AP.png')">Add to Cart</button>
       
    </div>
    <div class="product" style="display: inline-block; margin-right: 20px;">
        <img src="KILLSHOT+2+LTR+PRM.png" alt="Nike Killshot 2">
        <h3>Nike Killshot 2</h3>
        <p>$140.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesd">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Killshot 2', 'sizesd', 140.00, 'KILLSHOT+2+LTR+PRM.png')">Add to Cart</button>
        
    </div>
    <div class="product" style="display: inline-block;">
        <img src="AIR+MAX+270+SE+(GS).png" alt="Nike Air Max 270">
        <h3>Nike Air Max 270</h3>
        <p>$160.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesc">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Air Max 270', 'sizesc', 160.00, 'AIR+MAX+270+SE+(GS).png')">Add to Cart</button>
    </div>
     <div class="product" style="display: inline-block;">
        <img src="W+BLAZER+MID+77+VNTG.jpg" alt="Nike Blazer Mid '77">
        <h3>Nike Blazer Mid '77</h3>
        <p>$110.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesb">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Blazer Mid 77', 'sizesb', 110.00, 'W+BLAZER+MID+77+VNTG.jpg')">Add to Cart</button>
       
    </div>
    <div class="product" style="display: inline-block;">
        <img src="NIKE+CORTEZ.png" alt="Nike Cortez">
        <h3>Nike Cortez</h3>
        <p>$110.00</p>
        <label for="sizes">Select Size:</label>
        <select id="sizesa">
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
        </select><br><br>
        <button onclick="addToCart('Nike Cortez', 'sizesa', 110.00, 'NIKE+CORTEZ.png')">Add to Cart</button>
      
    </div>

</div>
<div id="products" style="overflow-x: auto; white-space: nowrap; padding: 20px;">
    <hr><br>
<!-- Shoe Image Slider -->
<div class="slider-container">
    <div class="slider">
        <img src="model1.jpg" alt="Shoe 1">
        <img src="Screenshot 2024-12-09 212843.png" alt="Shoe 2">
        <img src="thumb_118299_default_news_size_5.jpeg" alt="Shoe 3">
        <img src="JD_x_Nike_Swoosh-Season_02_Womens-Banners_1920px_x_840px.jpg" alt="Shoe 4">
        <img src="Nike-Training-Kit-main.jpg" alt="Shoe 5">
    </div>
</div>

<style>
    .view-more {
        background-color: #000;
        color: #fff;
        border: none;
        padding: 10px 20px;
        font-size: 16px;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s;
        margin: 20px auto;
        display: block;
    }

    .view-more:hover {
        background-color: #333;
    }
</style>
<style>
    /* Slider Container */
    .slider-container {
        margin: 40px auto;
        overflow: hidden;
        width: 100%; /* Adjust as per your design */
        max-width: 1200px;
    }

    /* Slider Content */
    .slider {
        display: flex;
        width: calc(100% * 5); /* Number of images */
        animation: slide 30s infinite linear;
    }

    /* Slider Images */
    .slider img {
        width: 20%; /* Divide evenly for 5 images */
        flex-shrink: 0;
    }

    /* Slider Animation */
    @keyframes slide {
        0% { transform: translateX(0); }
        100% { transform: translateX(-100%); }
    }
</style>
 




    <!-- Footer -->
    <footer>
        
        <p>© 2024 Nike Store. All rights reserved.</p>
    </footer>
    
    
  <script>
    function logout() {
    localStorage.removeItem('username'); // Remove the username
    localStorage.removeItem('cart'); // Clear the cart
    window.location.href = 'signin.html'; // Redirect to the sign-in page
}

  </script>
   
   <script>
    function addToCart(model, sizeId, price, image) {
        const size = document.getElementById(sizeId).value; // Get the selected size
        const item = { model, size, price, image }; // Create an item object
        const cart = JSON.parse(localStorage.getItem('cart')) || []; // Get existing cart or create a new one
        cart.push(item); // Add the new item to the cart
        localStorage.setItem('cart', JSON.stringify(cart)); // Save the updated cart to localStorage
        alert(${model} added to cart!); // Notify the user
        window.location.href = 'checkout.html'; // Redirect to the checkout page
    }
    function login(username) {
    localStorage.setItem('username', username); // Set the username
    localStorage.setItem('cart', JSON.stringify([])); // Initialize an empty cart
    window.location.href = 'index.html'; // Redirect to the home page
}

</script>
</body>
    <!-- JavaScript -->
    <script>
        function addToCart(product) {
            alert(product + " has been added to your cart!");
        }
    </script>
</body>
</html>
