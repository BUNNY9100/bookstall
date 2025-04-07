# bookstall
in these website u find all types of books
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Live Crypto Price</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #111;
      color: #0f0;
      padding-top: 50px;
    }
    #price {
      font-size: 3em;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Live BTC/USDT Price</h1>
  <div id="price">Loading...</div>

  <script>
    const priceElement = document.getElementById('price');

    // Connect to Binance WebSocket for BTC/USDT trade data
    const socket = new WebSocket('wss://stream.binance.com:9443/ws/btcusdt@trade');

    socket.onmessage = function(event) {
      const data = JSON.parse(event.data);
      const price = parseFloat(data.p).toFixed(2);
      priceElement.textContent = `$${price}`;
    };

    socket.onerror = function(error) {
      priceElement.textContent = 'Error loading data.';
      console.error('WebSocket error:', error);
    };
  </script>
</body>
</html>
