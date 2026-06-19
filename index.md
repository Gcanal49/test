<style>
  /* Reset y tipografía Pro */
  .shop-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    color: #1e293b;
    max-width: 1000px;
    margin: 0 auto;
    padding: 10px;
  }

  /* Encabezado de la tienda y botón del Carrito */
  .shop-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid #f1f5f9;
    padding-bottom: 15px;
    margin-bottom: 30px;
  }
  .cart-toggle-btn {
    background-color: #0f172a;
    color: white !important;
    border: none;
    padding: 10px 20px;
    border-radius: 9999px;
    font-weight: 600;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  /* Grid de Productos */
  .products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 24px;
  }
  .product-card {
    background: white;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0,0,0,0.04);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .product-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
  }
  .product-img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    background-color: #f8fafc;
  }
  .product-info {
    padding: 16px;
  }
  .product-title {
    font-size: 1.1rem;
    font-weight: 600;
    margin: 0 0 8px 0;
  }
  .product-price {
    font-size: 1.2rem;
    font-weight: 700;
    color: #2563eb;
    margin-bottom: 12px;
  }
  .btn-add-cart {
    background-color: #2563eb;
    color: white !important;
    width: 100%;
    border: none;
    padding: 10px;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
  }
  .btn-add-cart:hover { background-color: #1d4ed8; }

  /* Ventana Lateral del Carrito (Modal dialog) */
  #cartModal {
    border: none;
    border-radius: 16px;
    box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1), 0 10px 10px -5px rgba(0,0,0,0.04);
    padding: 24px;
    width: 90%;
    max-width: 450px;
  }
  #cartModal::backdrop {
    background: rgba(15, 23, 42, 0.4);
    backdrop-filter: blur(4px);
  }
  .cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid #e2e8f0;
  }
  .cart-total {
    font-size: 1.3rem;
    font-weight: 700;
    text-align: right;
    margin: 20px 0;
  }
  .btn-checkout {
    background-color: #22c55e;
    color: white !important;
    width: 100%;
    border: none;
    padding: 12px;
    border-radius: 8px;
    font-size: 1.1rem;
    font-weight: 700;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 8px;
  }
  .btn-checkout:hover { background-color: #16a34a; }
</style>

<div class="shop-container">

  <!-- ENCABEZADO -->
  <div class="shop-header">
    <div>
      <h1 style="margin:0; font-size: 1.8rem; color:#0f172a;">🛠️ Mundimotos Express</h1>
      <p style="margin:5px 0 0 0; color:#64748b;">Catálogo Digital de Repuestos y Accesorios</p>
    </div>
    <button class="cart-toggle-btn" onclick="openCart()">
      🛒 Carrito (<span id="cart-count">0</span>)
    </button>
  </div>

  <!-- GRID DE PRODUCTOS -->
  <div class="products-grid">
    
    <!-- Producto 1 -->
    <div class="product-card">
      <img src="https://images.unsplash.com/photo-1558981806-ec527fa84c39?w=400" class="product-img">
      <div class="product-info">
        <h3 class="product-title">Casco Integral Certificado</h3>
        <div class="product-price">$280.000</div>
        <button class="btn-add-cart" onclick="addToCart('Casco Integral Certificado', 280000)">Añadir al Carrito</button>
      </div>
    </div>

    <!-- Producto 2 -->
    <div class="product-card">
      <img src="https://images.unsplash.com/photo-1615887023516-9b6bcd559e87?w=400" class="product-img">
      <div class="product-info">
        <h3 class="product-title">Kit de Arrastre Premium</h3>
        <div class="product-price">$145.000</div>
        <button class="btn-add-cart" onclick="addToCart('Kit de Arrastre Premium', 145000)">Añadir al Carrito</button>
      </div>
    </div>

    <!-- Producto 3 -->
    <div class="product-card">
      <img src="https://images.unsplash.com/photo-1485965120184-e220f721d03e?w=400" class="product-img">
      <div class="product-info">
        <h3 class="product-title">Pastillas de Freno Sinterizadas</h3>
        <div class="product-price">$65.000</div>
        <button class="btn-add-cart" onclick="addToCart('Pastillas de Freno Sinterizadas', 65000)">Añadir al Carrito</button>
      </div>
    </div>

  </div>

</div>

<!-- MODAL DEL CARRITO (CHECKOUT) -->
<dialog id="cartModal">
  <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:20px;">
    <h2 style="margin:0; font-size:1.4rem;">🛍️ Tu Pedido</h2>
    <button onclick="closeCart()" style="background:none; border:none; font-size:1.2rem; cursor:pointer;">❌</button>
  </div>
  
  <div id="cart-items-container">
    <!-- Los productos agregados se renderizan aquí dinámicamente -->
  </div>
  
  <div class="cart-total">
    Total: <span id="cart-total-val">$0</span>
  </div>
  
  <button class="btn-checkout" onclick="sendWhatsAppCheckout()">
    💬 Confirmar y Pedir por WhatsApp
  </button>
</dialog>

<!-- MOTOR JAVASCRIPT DEL CARRITO -->
<script>
  // Arreglo global para almacenar los productos del carrito
  let cart = [];

  function addToCart(name, price) {
    // Buscar si el producto ya existe en el carrito
    const existingItem = cart.find(item => item.name === name);
    if (existingItem) {
      existingItem.quantity += 1;
    } else {
      cart.push({ name: name, price: price, quantity: 1 });
    }
    updateCartUI();
  }

  function updateCartUI() {
    // Actualizar el contador del botón superior
    const totalCount = cart.reduce((sum, item) => sum + item.quantity, 0);
    document.getElementById('cart-count').innerText = totalCount;

    // Actualizar los elementos dentro del modal
    const container = document.getElementById('cart-items-container');
    if(cart.length === 0) {
      container.innerHTML = '<p style="color:#64748b; text-align:center;">El carrito está vacío</p>';
      document.getElementById('cart-total-val').innerText = '$0';
      return;
    }

    container.innerHTML = '';
    let totalMoney = 0;

    cart.forEach((item, index) => {
      const itemTotal = item.price * item.quantity;
      totalMoney += itemTotal;
      
      container.innerHTML += `
        <div class="cart-item">
          <div>
            <strong style="display:block;">${item.name}</strong>
            <small style="color:#64748b;">${item.quantity} x $${item.price.toLocaleString('es-CO')}</small>
          </div>
          <div style="display:flex; align-items:center; gap:10px;">
            <span>$${itemTotal.toLocaleString('es-CO')}</span>
            <button onclick="removeFromCart(${index})" style="background:none; border:none; color:#ef4444; cursor:pointer;">🗑️</button>
          </div>
        </div>
      `;
    });

    document.getElementById('cart-total-val').innerText = '$' + totalMoney.toLocaleString('es-CO');
  }

  function removeFromCart(index) {
    cart.splice(index, 1);
    updateCartUI();
  }

  function openCart() {
    document.getElementById('cartModal').showModal();
  }

  function closeCart() {
    document.getElementById('cartModal').close();
  }

  function sendWhatsAppCheckout() {
    if(cart.length === 0) {
      alert('Añade al menos un producto para realizar el pedido.');
      return;
    }

    // Configura aquí tu número de WhatsApp (código de país + número, sin espacios ni el signo +)
    const phoneNumber = "573000000000"; 
    
    let message = "🤖 *Nuevo Pedido - Mundimotos Express*\n\n";
    let totalMoney = 0;

    cart.forEach(item => {
      const itemTotal = item.price * item.quantity;
      totalMoney += itemTotal;
      message += `▪️ ${item.quantity}x ${item.name} ($${itemTotal.toLocaleString('es-CO')})\n`;
    });

    message += `\n💰 *Total a pagar:* $${totalMoney.toLocaleString('es-CO')}\n\n`;
    message += "Por favor, confírmenme la disponibilidad para coordinar el pago y el envío. 👍";

    // Codificar el texto para que sea válido en una URL
    const encodedMessage = encodeURIComponent(message);
    const whatsappUrl = `https://api.whatsapp.com/send?phone=${phoneNumber}&text=${encodedMessage}`;

    // Abrir ventana de WhatsApp y limpiar carrito
    window.open(whatsappUrl, '_blank');
    cart = [];
    updateCartUI();
    closeCart();
  }
</script>
