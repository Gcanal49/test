<style>
  .markdown-section {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    color: #334155;
    line-height: 1.6;
  }
  
  /* Contenedor Flex para layouts modernos (Texto al lado de Imagen) */
  .flex-container {
    display: flex;
    gap: 24px;
    align-items: center;
    margin: 20px 0;
  }
  .flex-image {
    flex: 1;
    max-width: 250px;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }
  .flex-text { flex: 2; }

  /* Barra de progreso/expansión visual */
  .progress-bar-bg {
    background-color: #e2e8f0;
    border-radius: 9999px;
    width: 100%;
    height: 12px;
    margin: 8px 0 20px 0;
    overflow: hidden;
  }
  .progress-bar-fill {
    background: linear-gradient(90deg, #3b82f6, #10b981);
    height: 100%;
    width: 75%; /* Controla el porcentaje aquí */
    border-radius: 9999px;
  }

  /* Pop-up / Modal controlado por HTML nativo (<dialog>) */
  dialog {
    border: none;
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    padding: 24px;
    max-width: 400px;
  }
  dialog::backdrop {
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(4px);
  }
  
  /* Botones Pro */
  .btn {
    display: inline-block;
    padding: 10px 18px;
    border-radius: 6px;
    text-decoration: none;
    font-weight: 600;
    cursor: pointer;
    border: none;
  }
  .btn-primary { background-color: #3b82f6; color: white !important; }
  .btn-secondary { background-color: #64748b; color: white !important; }
</style>

# 🛒 Ficha de Componente: Módulo E-Commerce

Control de despliegue y empaquetado de assets para la plataforma web.

---

## 📸 Vista Previa del Módulo

<div class="flex-container">
  <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=500" class="flex-image" alt="Dashboard Preview">
  <div class="flex-text">
    <h3>E-Commerce Core v2.1</h3>
    <p>Este bloque integra el motor de renderizado de catálogos mediante carga asíncrona de archivos JSON y la gestión automatizada de pedidos por WhatsApp.</p>
    <button class="btn btn-primary" onclick="document.getElementById('myModal').showModal()">✨ Ver Credenciales de Prueba</button>
  </div>
</div>

---

## 📊 Estado de Implementación (75%)

Uso de barras de estado dinámicas y casillas interactivas[cite: 1]:
<div class="progress-bar-bg"><div class="progress-bar-fill"></div></div>

- [x] Estructura del backend en PHP[cite: 1].
- [x] Renderizado de componentes en React[cite: 1].
- [ ] Conexión final con pasarela de pagos[cite: 1].

---

## ⚙️ Configuración Avanzada

<details>
<summary>🛠️ Expandir parámetros de inicialización en cPanel</summary>

Si estás desplegando en subcarpetas de hosting tradicionales, asegúrate de estructurar el archivo `.htaccess` para no romper las rutas de la SPA:
```apache
RewriteEngine On
RewriteBase /tu-subcarpeta/
RewriteRule ^index\.html$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /tu-subcarpeta/index.html [L]
