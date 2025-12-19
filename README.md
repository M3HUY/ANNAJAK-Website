<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>ANAJAK International Store</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f2f2f2;
}
header {
  background: #000;
  color: white;
  padding: 15px;
  text-align: center;
}
.products {
  display: flex;
  justify-content: center;
  gap: 20px;
  padding: 20px;
  flex-wrap: wrap;
}
.card {
  background: white;
  width: 220px;
  padding: 15px;
  border-radius: 6px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
.card img {
  width: 100%;
  border-radius: 5px;
}
button {
  margin-top: 10px;
  padding: 8px;
  width: 100%;
  background: black;
  color: white;
  border: none;
  cursor: pointer;
}
.cart, .tracking {
  background: white;
  margin: 20px;
  padding: 15px;
  border-radius: 5px;
}
footer {
  background: #222;
  color: white;
  text-align: center;
  padding: 10px;
}
</style>
</head>

<body>

<header>
<h1>ANAJAK</h1>
<p>International Clothing Store</p>
<p>🛒 Cart Items: <span id="cartCount">0</span></p>
</header>

<section class="products">
  <div class="card">
    <img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab">
    <h3>T-Shirt</h3>
    <p>$25</p>
    <button onclick="addToCart('T-Shirt')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f">
    <h3>Hoodie</h3>
    <p>$45</p>
    <button onclick="addToCart('Hoodie')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1520975916090-3105956dac38">
    <h3>Jacket</h3>
    <p>$80</p>
    <button onclick="addToCart('Jacket')">Add to Cart</button>
  </div>
</section>

<div class="cart">
<h2>🧾 Order Checkout</h2>
<button onclick="checkout()">Place Order</button>
<p id="orderResult"></p>
</div>

<div class="tracking">
<h2>📦 Order Tracking</h2>
<input id="trackInput" placeholder="Enter Order ID">
<button onclick="trackOrder()">Track</button>
<p id="trackResult"></p>
</div>

<footer>
<p>© 2026 ANAJAK – Worldwide Shipping 🌍</p>
</footer>

<script>
let cart = [];
let orders = {};

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
    "✅ Order Placed! Your Order ID: " + orderId;
  cart = [];
  document.getElementById("cartCount").innerText = 0;
}

function trackOrder() {
  let id = document.getElementById("trackInput").value;
  if (orders[id]) {
    document.getElementById("trackResult").innerText =
      "📦 Order Status: " + orders[id];
  } else {
    document.getElementById("trackResult").innerText =
      "❌ Order ID not found";
  }
}
</script>

</body>
</html>

