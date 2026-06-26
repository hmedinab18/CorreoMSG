# 📧 Generador de Correos .MSG — Entel Perú

Crea archivos Outlook (.MSG) ya enviados directamente en el navegador. **Sin instalación, sin servidor, sin dependencias.**

🇵🇪 **Optimizado para Entel Perú** | 🚀 **Desplegado en Vercel** | 💾 **100% JavaScript**

---

## ✨ Características

✅ **Genera archivos .MSG reales** — Compatible con Outlook, Thunderbird y otros clientes de correo  
✅ **Marca como "Ya enviado"** — Los correos aparecen como enviados (MAPI_READ | MAPI_SENT)  
✅ **Sin backend** — Todo se ejecuta en el navegador (JavaScript puro)  
✅ **Plantilla Entel** — Asunto y cuerpo personalizados con datos de venta  
✅ **Descargas directas** — El archivo se guarda en descargas del usuario  
✅ **Móvil responsivo** — Funciona en desktop, tablet y teléfono  

---

## 🚀 Despliegue en Vercel (1 minuto)

### Opción 1: Desde GitHub (Recomendado)

1. **Fork o clona este repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/generador-msg-entel.git
   cd generador-msg-entel
   ```

2. **Push a tu repositorio GitHub:**
   ```bash
   git remote set-url origin https://github.com/tu-usuario/generador-msg-entel.git
   git push -u origin main
   ```

3. **Abre [https://vercel.com](https://vercel.com)**
   - Click en **"Add New..."** → **"Project"**
   - Selecciona tu repositorio
   - Click **"Deploy"**

4. **¡Listo!** Tu URL será algo como:
   ```
   https://generador-msg-entel.vercel.app
   ```

### Opción 2: Despliegue directo desde Vercel CLI

```bash
# Instala Vercel CLI
npm i -g vercel

# Deploy
vercel
```

---

## 📖 Uso

### 1. Abre la aplicación
```
https://tu-dominio.vercel.app
```

### 2. Completa el formulario

**Información del Cliente:**
- RUC: Número de RUC (ej: 20123456789)
- Razón Social: Nombre de la empresa
- Oportunidad: Número de venta (ej: 2026-06-001)
- Dirección: Domicilio de instalación

**Detalles del Servicio:**
- Plan: Selecciona de la lista
- Promoción: Tipo de oferta
- Plazo: Vigencia de la promoción

**Partes Involucradas:**
- Destinatario: Nombre del cliente
- Email destino: correo@cliente.com
- Email remitente: ventas@entel.pe

**Fecha y Hora:**
- Fecha de envío
- Hora de envío

### 3. Genera el correo

- **Vista Previa:** Revisa antes de generar
- **Generar y Descargar:** Crea el archivo .MSG
- **Limpiar:** Resetea el formulario

### 4. Abre en Outlook

El archivo .MSG se descargará como:
```
CONTRATO_INTERNET_FIJO_ENTEL_EMPRESA_RUC_OPP.msg
```

Doble clic para abrir en Outlook como un correo recibido.

---

## 🛠️ Desarrollo Local

### Requisitos
- Node.js 18+ (opcional, solo para servidor local)

### Instala dependencias
```bash
npm install
```

### Inicia servidor local
```bash
npm run dev
```

Abre: `http://localhost:3000`

---

## 📁 Estructura de archivos

```
.
├── index.html          ← Aplicación completa (HTML + CSS + JavaScript)
├── package.json        ← Configuración de Vercel
├── vercel.json         ← Rutas y rewrites de Vercel
├── README.md           ← Este archivo
└── .gitignore          ← Archivos ignorados en Git
```

---

## 🔍 Cómo funciona

### 1. **Recopila datos del formulario**
   - Valida campos obligatorios
   - Capitaliza nombres automáticamente

### 2. **Construye el correo**
   - **Asunto:** `CONTRATO INTERNET FIJO ENTEL // {Razón Social} // {RUC} // {Oportunidad}`
   - **Cuerpo:** Plantilla con datos de venta

### 3. **Genera estructura OLE2/MAPI**
   - Crea archivo .MSG válido
   - Marca como "Enviado" internamente

### 4. **Descarga en navegador**
   - Usuario descarga el archivo
   - Sin almacenamiento en servidor

---

## ⚙️ Personalización

### Cambiar planes y promociones

En `index.html`, busca:
```html
<select id="cmbPlan">
  <option value="Internet 30 Mbps">Internet 30 Mbps</option>
  <!-- Agregar más aquí -->
</select>
```

### Cambiar nombre del remitente

En `index.html`, línea ~500:
```javascript
fromName:'Ventas Entel',  // Cambiar aquí
```

### Cambiar template del cuerpo

En `index.html`, función `generateMSG()`:
```javascript
const body = `Estimado(a) ${capitalizeWords(d.des)}, buen día.
...
```

### Cambiar colores (Branding Entel)

En `index.html`, sección `:root`:
```css
--accent: #d61f46;  /* Rojo Entel */
```

---

## 🐛 Troubleshooting

### ❌ "El navegador bloquea la descarga"
**Solución:** Verifica la configuración de descargas del navegador. Algunos navegadores piden confirmación.

### ❌ "Outlook no reconoce el archivo"
**Solución:** Asegúrate de que la extensión sea `.msg` (no `.msg.msg`). Verifica que Outlook esté instalado.

### ❌ "Los campos están vacíos"
**Solución:** Completa todos los campos con "*" rojo. Verifica que hayas seleccionado opciones en los dropdowns.

### ❌ "Error en JavaScript"
**Solución:** Abre la consola (F12 → Console) y copia el error. Reporta en Issues.

---

## 📝 Notas técnicas

- **Formato:** OLE2 Container (Microsoft Structured Storage)
- **MAPI Properties:** Message flags, sender, recipient, subject, body, timestamps
- **Cifrado:** NONE (archivos planos)
- **Tamaño:** ~1-2 KB por correo
- **Compatibilidad:** Windows, Mac, Linux

---

## 🔒 Privacidad

✅ **Sin recopilación de datos**
- Todos los datos se procesan en el navegador
- No se envía nada a servidores
- No hay cookies ni tracking

---

## 📄 Licencia

MIT — Libre de usar y modificar

---

## 👨‍💼 Soporte

¿Preguntas o sugerencias?

- **Issues:** Abre un issue en GitHub
- **Mejoras:** Fork → Modifica → Pull Request
- **Contacto:** (Tu email aquí)

---

## 🎯 Roadmap

- [ ] Agregar adjuntos a correos
- [ ] Plantillas personalizadas por usuario
- [ ] Exportar múltiples correos (ZIP)
- [ ] Historial de correos generados
- [ ] Autenticación con Google para guardar datos
- [ ] Integración con Outlook API

---

## 🙏 Créditos

- **MAPI/OLE2 Implementation:** JavaScript puro
- **UI Framework:** Diseño custom + Inter fonts
- **Hosting:** Vercel (gratuito)

---

**Hecho con ❤️ para Entel Perú**

*v1.0.0 — 2026*
