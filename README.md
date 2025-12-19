<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>ANAJAK International Store</title>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', Arial, sans-serif;
  background: #f4f6f8;
}

/* HEADER */
header {
  background: linear-gradient(90deg, #111, #333);
  color: white;
  padding: 15px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.logo h1 {
  margin: 0;
  font-size: 22px;
}

.user {
  font-size: 14px;
}

/* BUTTONS */
button {
  padding: 10px;
  border-radius: 25px;
  border: none;
  cursor: pointer;
  font-weight: bold;
  transition: 0.3s;
}

.btn-primary {
  background: linear-gradient(45deg, #ff6a00, #ee0979);
  color: white;
}

.btn-primary:hover {
  opacity: 0.85;
}

.btn-secondary {
  background: linear-gradient(45deg, #2193b0, #6dd5ed);
  color: white;
}

/* PRODUCTS */
.products {
  display: flex;
  justify-content: center;
  gap: 20px;
  padding: 30px;
  flex-wrap: wrap;
}

.card {
  background: white;
  width: 220px;
  padding: 15px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 0 10px 20px rgba(0,0,0,0.1);
}

.card img {
  width: 100%;
  border-radius: 10px;
}

/* SECTIONS */
.section {
  background: white;
  margin: 20px;
  padding: 20px;
  border-radius: 10px;
}

input {
  padding: 8px;
  width: 200px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

/* FOOTER */
footer {
  background: #111;
  color: white;
  text-align: center;
  padding: 15px;
}
</style>
</head>

<body>

<header>
  <div class="logo">
    <!-- REAHU LOGO -->
    <img src="https://i.imgur.com/Z6f7K9Q.png" alt="Reahu Logo">
    <h1>ANAJAK</h1>
  </div>

  <div class="user">
    👤 <span id="username">Guest</span>
    <button class="btn-secondary" onclick="login()">Login</button>
  </div>
</header>

<section class="products">
  <div class="card">
    <img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab">
    <h3>T-Shirt</h3>
    <p>$25</p>
    <button class="btn-primary" onclick="addToCart('T-Shirt')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f">
    <h3>Hoodie</h3>
    <p>$45</p>
    <button class="btn-primary" onclick="addToCart('Hoodie')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1520975916090-3105956dac38">
    <h3>Jacket</h3>
    <p>$80</p>
    <button class="btn-primary" onclick="addToCart('Jacket')">Add to Cart</button>
  </div>
</section>

<div class="section">
  🛒 Cart Items: <b><span id="cartCount">0</span></b><br><br>
  <button class="btn-primary" onclick="checkout()">Place Order</button>
  <p id="orderResult"></p>
</div>

<div class="section">
  <h3>📦 Order Tracking</h3>
  <input id="trackInput" placeholder="Enter Order ID">
  <button class="btn-secondary" onclick="trackOrder()">Track</button>
  <p id="trackResult"></p>
</div>

<footer>
  © 2026 ANAJAK – Designed with REAHU 🌍
</footer>

<script>
let cart = [];
let orders = {};
let user = "Guest";

function login() {
  user = prompt("Enter your username:");
  if (user) {
    document.getElementById("username").innerText = user;
  }
}

function addToCart(product) {
  cart.push(product);
  document.getElementById("cartCount").innerText = cart.length;
}

function checkout() {
  if (cart.length === 0) {
    alert("Cart is empty!");
    return;
  }
  let orderId = "ANJ" + Math.floor(Math.random() * 100000);
  orders[orderId] = "Processing";
  document.getElementById("orderResult").innerText =
    "✅ Order placed by " + user + ". Order ID: " + orderId;
  cart = [];
  document.getElementById("cartCount").innerText = 0;
}

function trackOrder() {
  let id = document.getElementById("trackInput").value;
  if (orders[id]) {
    document.getElementById("trackResult").innerText =
      "📦 Status: " + orders[id];
  } else {
    document.getElementById("trackResult").innerText =
      "❌ Order not found";
  }
}
</script>

</body>
</html>


