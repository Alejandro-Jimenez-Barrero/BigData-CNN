# Inventario Automático con YOLO + ONNX Runtime Web

Este módulo forma parte del proyecto **BigData-CNN** y permite realizar **detección de objetos en imágenes directamente desde el navegador**, sin necesidad de servidor, usando:

- **YOLOv8 exportado a ONNX** (salida 1×300×6 con NMS integrado)
- **ONNX Runtime Web (WASM)**
- **JavaScript + Canvas** para visualizar detecciones

La aplicación detecta únicamente las siguientes clases relevantes para inventario:

- **15:** mouse
- **16:** silla
- **18:** mesa
- **19:** teclado
- **20:** cpu
- **21:** pantalla

---

## 🚀 Características
- Ejecución **100% local en el navegador**.
- No requiere backend, Python ni servidores.
- Modelo ONNX ligero optimizado para WebAssembly.
- Dibuja bounding boxes y genera un conteo automático.
- Compatible con GitHub Pages.

---

## 📂 Estructura del módulo
```
inventario/
│── index.html         # Aplicación web completa
│── best.onnx          # Modelo YOLO exportado a ONNX
└── README.md          # Este archivo
```

---

## 🌐 Ejecución en GitHub Pages
Cuando el repositorio tiene habilitado GitHub Pages, la aplicación puede ejecutarse directamente desde la web:

```
https://<USUARIO>.github.io/BigData-CNN/inventario/index.html
```

⚠ Asegúrate de que:
- `index.html` y `best.onnx` estén en la misma carpeta.
- El código use la ruta relativa:
  ```js
  ort.InferenceSession.create("best.onnx")
  ```

---

## ▶️ Ejecución local
Puedes ejecutar el proyecto localmente con un servidor simple:

```bash
cd inventario
python3 -m http.server 8000
```
Luego abre en el navegador:
```
http://localhost:8000/index.html
```

---

## 📸 Cómo usarlo
1. Abre la página.
2. Carga una imagen desde el botón.
3. El sistema ejecuta el modelo ONNX.
4. Se generan:
   - bounding boxes
   - etiquetas de clase
   - puntaje de confianza
   - conteo total por tipo de objeto

---

## 🧠 Modelo YOLO utilizado
- Entrenado con **YOLOv8n**
- Exportado a **ONNX** con salida 1×300×6:
  ```
  [x1, y1, x2, y2, score, class]
  ```
- Incluye **NMS integrado**.
- Optimizado para entrada **320×320**.

---

## 🛠 Tecnologías
- **ONNX Runtime Web** (WASM backend)
- HTML5 + JavaScript
- Canvas 2D API
- YOLOv8 → ONNX (Ultralytics)

---

## 📌 Notas
- Si el modelo es mayor a 100MB, usa **Git LFS**.
- El navegador debe permitir ejecución WASM (todos los modernos).
- GitHub Pages puede tardar ~1 minuto en actualizar cambios.

---

## 📧 Contacto
Desarrollado por **Alejandro Jiménez Barrero** como parte del proyecto **BigData-CNN**.

Si deseas extender la aplicación (detección en video, cámara web, dashboards, exportación CSV), puedo ayudarte.

