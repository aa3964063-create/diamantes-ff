index.html

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Recarga Games</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #0a0a0f, #1a1a2e);
      color: white;
      text-align: center;
      margin: 0;
    }

    h1 {
      margin-top: 20px;
      font-size: 2.5rem;
      color: #ff4136;
    }

    .container {
      max-width: 600px;
      margin: auto;
      padding: 20px;
    }

    input, select {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border-radius: 10px;
      border: none;
      font-size: 16px;
    }

    button {
      width: 100%;
      padding: 14px;
      background: linear-gradient(90deg, #ff4136, #ff9f1c);
      border: none;
      border-radius: 30px;
      color: white;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
    }

    .card {
      background: #111;
      padding: 15px;
      border-radius: 15px;
      margin: 10px 0;
    }

    .price-box {
      background: #000;
      padding: 10px;
      border-radius: 10px;
      margin-top: 10px;
      font-size: 16px;
    }

    .floating-btn {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #25D366;
      padding: 15px;
      border-radius: 50%;
      font-size: 20px;
      cursor: pointer;
    }

    .info {
      margin-top: 15px;
      font-size: 14px;
      color: #ccc;
    }

    .payment-box {
      background: #000;
      padding: 10px;
      border-radius: 10px;
      margin-top: 15px;
      font-size: 14px;
    }
  </style>
</head>
<body>

  <h1>🎮 Recarga Games</h1>

  <div class="container">

    <div class="card">
      <h3>Selecciona tu compra</h3>

      <input type="text" id="uid" placeholder="Ingresa tu UID">

      <select id="producto" onchange="actualizarPrecio()">
        <option value="110 Diamantes|660">110 💎 - 660 Bs</option>
        <option value="220 Diamantes|1320">220 💎 - 1320 Bs</option>
        <option value="341 Diamantes|2210">341 💎 - 2210 Bs</option>
        <option value="572 Diamantes|3370">572 💎 - 3370 Bs</option>
        <option value="1166 Diamantes|6255">1166 💎 - 6255 Bs</option>
        <option value="2398 Diamantes|12765">2398 💎 - 12765 Bs</option>
        <option value="6160 Diamantes|32430">6160 💎 - 32430 Bs</option>
        <option value="Tarjeta Semanal Básica|503">Tarjeta Semanal Básica - 503 Bs</option>
        <option value="Tarjeta Semanal|1725">Tarjeta Semanal - 1725 Bs</option>
        <option value="Tarjeta Mensual|7400">Tarjeta Mensual - 7400 Bs</option>
        <option value="Pase Booyah|1250">Pase Booyah - 1250 Bs</option>
        <option value="Pase de Nivel|2760">Pase de Nivel - 2760 Bs</option>
      </select>

      <div class="price-box" id="precioBox">
        💰 Precio: -
      </div>

      <select id="pago">
        <option>Pago Móvil</option>
        <option>Binance</option>
      </select>

      <!-- NUEVO: REFERENCIA DE PAGO -->
      <input type="text" id="referencia" placeholder="Referencia del pago (opcional)">

      <button onclick="comprar()">Comprar ahora</button>

      <div class="payment-box">
        🏦 Pago Móvil:<br>
        Bancamiga<br>
        0172<br>
        32824869<br>
        04264696162
      </div>

      <div class="info">
        ⏱️ Entrega de 10 a 15 minutos<br>
        📧 Soporte: cameroangel525@gmail.com<br>
        📞 Atención: 04228242411
      </div>
    </div>

  </div>

  <div class="floating-btn" onclick="soporte()">💬</div>

  <script>
    const phone = "584123456789"; // CAMBIA ESTO

    function actualizarPrecio() {
      const productoRaw = document.getElementById("producto").value;
      const [nombre, bs] = productoRaw.split("|");

      document.getElementById("precioBox").innerHTML =
        `💰 ${bs} Bs`;
    }

    function comprar() {
      const uid = document.getElementById("uid").value;
      const productoRaw = document.getElementById("producto").value;
      const [nombre, bs] = productoRaw.split("|");
      const pago = document.getElementById("pago").value;
      const referencia = document.getElementById("referencia").value;

      if (!uid) {
        alert("Ingresa tu UID");
        return;
      }

      if (!/^\\d+$/.test(uid)) {
        alert("El UID debe ser numérico");
        return;
      }

      const mensaje = `🛒 PEDIDO%0AUID: ${uid}%0AProducto: ${nombre}%0A💰 ${bs} Bs%0A💳 Pago: ${pago}%0A📌 Referencia: ${referencia || 'No enviada'}`;

      window.open(`https://wa.me/${phone}?text=${mensaje}`, "_blank");
    }

    function soporte() {
      window.open(`https://wa.me/${phone}?text=Hola, necesito información`, "_blank");
    }

    actualizarPrecio();
  </script>

</body>
</html>
