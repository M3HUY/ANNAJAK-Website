<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>ANAJAK International Store</title>

<style>
* { font-family: "Times New Roman", Times, serif; }

body { margin: 0; background: #f4f6f8; }

header {
  background: linear-gradient(90deg, #000, #222);
  color: gold;
  padding: 15px 25px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo { display: flex; align-items: center; gap: 15px; }
.logo img { width: 55px; }
.logo h1 { margin: 0; }

button {
  padding: 10px 18px;
  border-radius: 25px;
  border: none;
  cursor: pointer;
}

.btn-primary {
  background: linear-gradient(45deg, gold, #caa300);
}

.btn-secondary {
  background: linear-gradient(45deg, #333, #111);
  color: gold;
}

.products {
  display: flex;
  justify-content: center;
  gap: 25px;
  padding: 30px;
  flex-wrap: wrap;
}

.card {
  background: white;
  width: 240px;
  padding: 15px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0,0,0,0.15);
}

.card img { width: 100%; border-radius: 10px; }

.section {
  background: white;
  margin: 20px;
  padding: 20px;
  border-radius: 10px;
}

footer {
  background: black;
  color: gold;
  text-align: center;
  padding: 15px;
}

/* MODAL */
.modal {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.6);
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: white;
  padding: 20px;
  width: 300px;
  border-radius: 12px;
  text-align: center;
}
</style>
</head>

<body>

<header>
  <div class="logo">
    <img src="reahu-logo.png">
    <h1>ANAJAK</h1>
  </div>
  <div>
    👤 <span id="user">Guest</span>
    <button class="btn-secondary" onclick="login()">Login</button>
  </div>
</header>

<section class="products">
  <div class="card">
    <img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab">
    <h3>T-Shirt</h3>
    <p>$25</p>
    <button class="btn-primary" onclick="details('T-Shirt',25)">View Details</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f">
    <h3>Hoodie</h3>
    <p>$45</p>
    <button class="btn-primary" onclick="details('Hoodie',45)">View Details</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1520975916090-3105956dac38">
    <h3>Jacket</h3>
    <p>$80</p>
    <button class="btn-primary" onclick="details('Jacket',80)">View Details</button>
  </div>
</section>

<div class="section">
  🌍 Shipping Country:
  <select id="country" onchange="updateShipping()">
    <option value="5">Cambodia ($5)</option>
    <option value="15">Thailand ($15)</option>
    <option value="25">Japan ($25)</option>
    <option value="30">USA ($30)</option>
  </select>

  <p>🧾 Total: $<span id="total">0</span></p>
  <button class="btn-primary" onclick="checkout()">Place Order</button>
  <p id="orderMsg"></p>
</div>

<div class="section">
  📦 Order Tracking<br>
  <input id="trackId" placeholder="Order ID">
  <button class="btn-secondary" onclick="track()">Track</button>
  <p id="trackResult"></p>
</div>

<footer>© 2026 ANAJAK – REAHU</footer>

<!-- MODAL -->
<div class="modal" id="modal">
  <div class="modal-content">
    <h3 id="mName"></h3>
    <p>Price: $<span id="mPrice"></span></p>
    <button class="btn-primary" onclick="add()">Add to Cart</button><br><br>
    <button onclick="closeModal()">Close</button>
  </div>
</div>

<script>
let cartPrice = 0;
let shipping = 5;
let orders = {};
let currentPrice = 0;

function login() {
  let u = prompt("Enter username (admin for admin):");
  if (u) document.getElementById("user").innerText = u;
}

function details(name, price) {
  currentPrice = price;
  document.getElementById("mName").innerText = name;
  document.getElementById("mPrice").innerText = price;
  document.getElementById("modal").style.display = "flex";
}

function closeModal() {
  document.getElementById("modal").style.display = "none";
}

function add() {
  cartPrice += currentPrice;
  updateShipping();
  closeModal();
}

function updateShipping() {
  shipping = parseInt(document.getElementById("country").value);
  document.getElementById("total").innerText = cartPrice + shipping;
}

function checkout() {
  if (cartPrice === 0) return alert("Cart empty");
  let id = "ANJ" + Math.floor(Math.random()*10000);
  orders[id] = "Shipped";
  document.getElementById("orderMsg").innerText = "Order ID: " + id;
  cartPrice = 0;
  updateShipping();
}

function track() {
  let id = document.getElementById("trackId").value;
  document.getElementById("trackResult").innerText =
    orders[id] ? orders[id] : "Not Found";
}
</script>

</body>
</html>



