# Inventario Automático con YOLO + ONNX Runtime Web

Este módulo forma parte del proyecto **BigData-CNN** y permite realizar **detección de objetos en imágenes directamente desde el navegador**, sin necesidad de servidor, usando:

- **YOLOv8 exportado a ONNX** (salida 1×300×6 con NMS integrado)
- **ONNX Runtime Web (WASM)**
- **JavaScript + Canvas** para visualizar detecciones

La aplicación detecta únicamente las siguientes clases relevantes para inventario:

- **0:** mouse
- **1:** silla
- **2:** mesa
- **3:** teclado
- **4:** cpu
- **5:** pantalla


## 📂 Estructura del módulo
```
inventario/
│── index.html         # Aplicación web completa
│── best.onnx          # Modelo YOLO exportado a ONNX
│── best.h5            # Archivo de pesos en formato h5
│── best_int8.tflite   # Modelo YOLO en formato TensorFlow Lite
│── soportes
            └── │── Proyecto Inventario Big Data CNN.PDF # Informe corto del proyecto en formato PDF.
                │── Salón005.jpeg                        # Imagen de prueba para probar la aplicación.
                │── Prueba_TFLite.ipynb                  # Notebook de google colab con el entrenamiento del modelo. 
└── README.md          # Este archivo
```
---

## 🚀 Características
- Ejecución **100% local en el navegador**.
- No requiere backend, Python ni servidores.
- Modelo ONNX ligero optimizado para WebAssembly.
- Dibuja bounding boxes y genera un conteo automático.
- Compatible con GitHub Pages.
  
## 🌐 IMPORTANTE  EJECUCIÓN EN GitHub Pages: 
---
LINK PARA EJECUCIÓN DE APLICATIVO: https://alejandro-jimenez-barrero.github.io/BigData-CNN/inventario/index.html
---

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
2. Carga una imagen desde el botón. Puede ser la imagen de prueba subida en la carpeta Soporte de este repositorio: Salón005.jpeg
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
- TensorFlow Lite fue usado, sin embargo, se tuvieron problemas de compatibilidad con navegadores.

---

## 📌 Notas
- El modelo es funcional y cumple con algunos de los requerimientos del proyecto.
- Se ibtienen untajes de confianza aceptables con los onjetos identificados, sin embargo, aun faltan varios por ser identificados.
- Como se ha mencionado, al realizar la exportación del modelo en formato tflite (TensorFlow Lite), se tuvieron problemas de compatibilidad en la ejecución de la aplicación web, por lo que se optó por la ejecución del modelo en formato ONNX, obteniendo los mismos resultados esperados que con el modelo tflite.

---

## 📧 Contacto
Desarrollado por **Alejandro Jiménez Barrero - cód 20242695001** como parte del proyecto final del módulo **BigData-CNN**.


