# Multimodal-DeepLearning-IntegratedSystem  
### Sistema Integrado de Visión, PLN y Generación Sintética (EA1 + EA2 + EA3)

[![Status](https://img.shields.io/badge/status-Prototipo-blue)](#)
[![Python](https://img.shields.io/badge/Python-3.10+-yellow)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📌 Descripción General

Este repositorio contiene un sistema multimodal completamente integrado, desarrollado como proyecto académico para demostrar la sinergia entre:

- **Visión por Computadora (EA1):** Clasificación visual basada en heurísticas simples  
- **Procesamiento de Lenguaje Natural (EA2):** Análisis de sentimientos por lexicón  
- **Inteligencia Artificial Generativa (EA3):** Generación sintética mediante Perlin Noise  

El objetivo principal es mostrar cómo diferentes técnicas fundamentales de deep learning pueden trabajar juntas dentro de un pipeline unificado, con un enfoque modular, reproducible y visualmente interactivo mediante **Gradio**. La solución está optimizada para su uso en Kaggle, ejecución local y entornos educativos.

---

## 📂 Estructura del Repositorio

.
├─ README.md
├─ LICENSE
├─ requirements.txt
│
├─ notebooks/
│ ├─ Aguilar_Adriana_Villa_Edwin_EA4_Integracion_NB.ipynb
│ 


yaml
Copiar código

---

## 🧠 Arquitectura del Sistema

El sistema multimodal sigue el siguiente flujo:

Usuario → Pipeline → (EA1 + EA2 + EA3) → Salida Integrada

yaml
Copiar código

**Componentes:**
- EA1: análisis visual mediante estadísticas de imagen  
- EA2: análisis de sentimiento a partir de palabras clave  
- EA3: generador de patrones sintéticos con Perlin Noise  
- Pipeline: orquestación de los tres módulos  
- Interfaz: control e interacción mediante Gradio  

Los diagramas de arquitectura y roadmap se encuentran en:
- `assets/architecture_diagram.dot`
- `assets/roadmap.dot`

---

## 🧩 Componentes del Modelo

### 🟦 EA1 — Clasificación Visual  
Basado en:
- Brillo promedio  
- Desviación estándar  
- Softmax para probabilidad final  
Produce tres clases: **Persona**, **Objeto**, **Paisaje**.

### 🟩 EA2 — Análisis de Sentimientos  
Analiza un texto e identifica palabras:
- Positivas  
- Negativas  
Determina el sentimiento como: **Positivo**, **Negativo**, o **Neutral**.

### 🟥 EA3 — Generación Sintética  
Generador procedural con:
- Perlin básico  
- Multi-Octave (4 capas)
- Colorizado RGB  

### 🔀 Pipeline Integrado  
Ejecuta los tres componentes en secuencia y produce:
- Resultado de visión  
- Resultado de PLN  
- Imagen sintética  

---

## 🖥️ Instalación

### ✔️ Instalación en Kaggle (recomendada)

!pip install gradio==3.41.2 --no-deps -q
!pip install pillow numpy -q

shell
Copiar código

### ✔️ Instalación local

python -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

go
Copiar código

`requirements.txt` recomendado:

gradio==3.50.2
numpy
pillow
torch

yaml
Copiar código

---

## ▶️ Ejecución

### Ejecutar interfaz interactiva

python src/gradio_app.py

yaml
Copiar código

Luego abrir en el navegador:

http://127.0.0.1:7860

shell
Copiar código

### Ejecutar pipeline desde Python

from src.pipeline import pipeline_integrado
from PIL import Image

img = Image.new("RGB", (128,128))

vision, sentimiento, sintesis = pipeline_integrado(
img,
"Este es un día maravilloso",
42,
"Colorizado"
)

print(vision)
print(sentimiento)
sintesis.show()

yaml
Copiar código

---

## 🧪 Pruebas Unitarias

pytest -q

makefile
Copiar código

Ejemplo:

def test_pipeline_runs():
from PIL import Image
img = Image.new("RGB", (128,128))
v,s,g = pipeline_integrado(img, "prueba", 1, "Perlin")
assert isinstance(v, str)
assert isinstance(s, str)
assert hasattr(g, "size")

yaml
Copiar código

---

## 🧭 Roadmap Futuro

- Migrar EA1 → MobileNetV3 o EfficientNet  
- Migrar EA2 → Transformers (DistilBERT)  
- Migrar EA3 → GAN o modelos de difusión  
- Unificación del pipeline en FastAPI  
- Dockerización completa  
- Deploy en AWS / Azure / Google Cloud  
- Integración de autenticación, logging y métricas  
- Entrenamiento con dataset propio  

---

## 📚 Bibliografía

- Goodfellow, I. — *Deep Learning*. MIT Press  
- Chollet, F. — *Deep Learning with Python*  
- Perlin, K. — *An Image Synthesizer*  
- Vaswani et al. — *Attention is All You Need*  
- Jurafsky & Martin — *Speech and Language Processing*  
- O’Reilly — *Generative Deep Learning*  

---

## 📝 Licencia

Este proyecto está bajo la licencia **MIT**.  
Puedes reutilizarlo y modificarlo libremente.

---

## ✉️ Contacto

**Autores:** Adriana Aguilar y Edwin Villa






