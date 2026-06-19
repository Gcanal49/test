<style>
  /* Cambiar a una tipografía moderna del sistema y mejorar el espaciado */
  .markdown-section {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    color: #2c3e50;
    line-height: 1.6;
  }
  
  /* Personalizar los títulos principales con un color de marca (ej. Azul Oscuro) */
  .markdown-section h1, .markdown-section h2 {
    color: #1a365d;
    border-bottom: none;
    font-weight: 700;
  }

  /* Diseñar una tabla estilizada y limpia */
  .markdown-section table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
    font-size: 0.95rem;
  }
  .markdown-section th {
    background-color: #f7fafc;
    color: #4a5568;
    font-weight: 600;
    border-bottom: 2px solid #e2e8f0;
    padding: 12px;
  }
  .markdown-section td {
    padding: 12px;
    border-bottom: 1px solid #edf2f7;
  }

  /* Convertir enlaces específicos en botones Pro */
  .markdown-section .btn-primario {
    display: inline-block;
    background-color: #3182ce; /* Azul vibrante */
    color: #ffffff !important;
    padding: 10px 20px;
    border-radius: 6px;
    text-decoration: none;
    font-weight: 600;
    transition: background 0.2s ease;
    margin-top: 10px;
  }
  .markdown-section .btn-primario:hover {
    background-color: #2b6cb0;
  }
</style>

# 🚀 Lanzamiento de Proyecto: E-Commerce Repuestos

Bienvenido a la documentación oficial del desarrollo de la tienda en línea. Este sitio está generado dinámicamente desde un archivo de texto plano.

---

## 📌 Estado de Tareas

- [x] Configuración inicial del repositorio de código.
- [x] Maquetación de la interfaz responsive (Adaptable a móviles).
- [ ] Implementación de la pasarela de pagos.

[Ir al Repositorio Principal](# ':class=btn-primario')

---

## 📊 Comparativa de Módulos

| Componente | Tipo de Carga | Prioridad |
| :--- | :---: | :---: |
| Catálogo de productos | Dinámica (JSON) | **Alta** |
| Formulario de contacto | Estática (HTML) | Media |
| Panel de administración | Protegido | **Alta** |

---

## 💡 Preguntas Frecuentes

<details>
<summary>🔍 ¿Cómo se actualizan los precios en el sitio web?</summary>
Los precios se sincronizan mediante un backend ligero en PHP que lee un archivo de datos estructurado de forma automática cada hora.
</details>

<details>
<summary>📱 ¿La interfaz soporta visualización en tablets y teléfonos?</summary>
Sí, todo el diseño utiliza componentes CSS flexibles que se adaptan a cualquier resolución de pantalla.
</details>
