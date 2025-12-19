<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ANAJAK International Store</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f4f4f4;
    }
    header {
      background: black;
      color: white;
      padding: 15px;
      text-align: center;
    }
    .products {
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 20px;
    }
    .card {
      background: white;
      padding: 15px;
      width: 200px;
      border-radius: 5px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      text-align: center;
    }
    button {
      background: black;
      color: white;
      border: none;
      padding: 8px;
      cursor: pointer;
    }
    footer {
      text-align: center;
      padding: 10px;
      background: #222;
      color: white;
    }
  </style>
</head>
<body>

<header>
  <h1>ANAJAK</h1>
  <p>International Clothing Store</p>
</header>

<section class="products">
  <div class="card">
    <h3>ANAJAK T-Shirt</h3>
    <p>$25</p>
    <button>Add to Cart</button>
  </div>

  <div class="card">
    <h3>ANAJAK Hoodie</h3>
    <p>$45</p>
    <button>Add to Cart</button>
  </div>

  <div class="card">
    <h3>ANAJAK Jacket</h3>
    <p>$80</p>
    <button>Add to Cart</button>
  </div>
</section>

<footer>
  <p>© 2026 ANAJAK – International Shipping Available</p>
</footer>

</body>
</html>
