# 📊 Plataforma de Análisis Electoral — Dashboard Neo-Brutalista

Dashboard frontend interactivo construido en **JavaScript puro**, que consume un archivo `data.json` y presenta análisis estructurado de candidatos políticos mediante visualizaciones modernas, rankings y reportes detallados.

El sistema está diseñado con una estética **neo-brutalista / prensa digital**, priorizando claridad, jerarquía visual y lectura crítica de datos.

---

## 🚀 Características principales

- 📁 Carga dinámica de datos desde `data.json`
- 🏆 Ranking **Top 3 por Viabilidad Electoral**
- 🧠 Ranking **Top 3 por Confianza Institucional (IA)**
- 📊 Grid completo de candidatos clasificados por riesgo
- 🔎 Filtro por ideología y buscador en tiempo real
- 📑 Sidebar con **reporte detallado tipo informe periodístico**
- 🎨 Estética neo-brutalista moderna (sin frameworks JS)

---

## 🧱 Estructura general

- /index.html
- /data.json


El script principal vive dentro de un `<script>` en `index.html` y controla toda la lógica de renderizado.

---

## 📦 Estructura esperada de `data.json`

Cada candidato debe seguir este esquema:

```json
{
  "nombre": "Nombre del candidato",
  "partido": "Partido político",
  "ideologia_general": "Descripción ideológica",
  "viabilidad_electoral": {
    "estimacion": 65,
    "justificacion": "Análisis de contexto electoral"
  },
  "confianza_institucional_ia": {
    "porcentaje": 72,
    "criterios": [
      "Historial público verificable",
      "Ausencia de procesos activos"
    ]
  },
  "juicio_institucional_final": {
    "clasificacion": "apto | apto_con_reservas | alto_riesgo | no_apto",
    "fundamento": "Resumen del veredicto"
  },
  "denuncias_y_procesos": {
    "nivel": "bajo | medio | alto",
    "detalle": "Descripción",
    "estado_legal": "Investigación / Sentenciado / Archivado"
  },
  "experiencia_gestion": {
    "sector_publico": "Detalle",
    "sector_privado": "Detalle"
  },
  "fuentes": [
    {
      "medio": "Nombre del medio",
      "fecha": "2025-01-01",
      "enlace": "https://..."
    }
  ]
}```

## ⚙️ Flujo de funcionamiento

### 1️⃣ Carga de datos

La aplicación se inicializa automáticamente al cargar la página.

window.onload = loadData;

Proceso:
- Se realiza fetch('data.json')
- La información se almacena en la variable global allData
- Se inicializan todas las vistas del dashboard

⚠️ **Requiere servidor local**  
No funciona abriendo el HTML directamente (file://).  
Es obligatorio usar un servidor local.

### 2️⃣ Rankings superiores

#### 🏆 Top Viabilidad Electoral

Función:  
renderTopPodium(data)

- Ordena los candidatos por viabilidad_electoral.estimacion
- Selecciona los 3 valores más altos
- Renderiza un podio visual con estilo de prensa digital

#### 🧠 Top Confianza Institucional

Función:  
renderTopConfianza(data)

- Ordena por confianza_institucional_ia.porcentaje
- Muestra los candidatos más confiables según análisis de IA

### 3️⃣ Grid principal de candidatos

Función:  
renderGrid(data)

Clasificación automática:
- **Apto** → Verde
- **Apto con reservas** → Ámbar
- **Alto riesgo / No apto** → Rojo

Normalización interna de clasificaciones:

"Apto con reservas" → "apto_con_reservas"

Cada tarjeta incluye:
- Nombre del candidato
- Partido político
- Barra visual de confianza institucional
- Indicador semántico de riesgo
- Acceso al reporte completo (sidebar)

### 4️⃣ Interacción

#### 📌 Click en candidato

Función:  
handleCardClick()

Acción:
- Abre un sidebar lateral con el reporte detallado

Contenido del sidebar:
- Ideología general
- Métricas clave
- Denuncias y nivel de riesgo
- Veredicto institucional final
- Experiencia de gestión
- Fuentes verificables

#### ❌ Cierre del sidebar

Función:  
closeSidebar()

### 5️⃣ Filtros y búsqueda

#### Filtro por ideología

filterBy('izquierda')

#### Búsqueda libre

searchCandidato('nombre o partido')

La búsqueda analiza:
- Nombre del candidato
- Partido político
- Ideología general

## 🎨 Diseño y estilo

- Inspirado en prensa política digital
- Bordes sólidos de 2px
- Sombras duras tipo impresión editorial
- Colores semánticos:
  - Verde → confiable
  - Ámbar → observación
  - Rojo → riesgo
- Sin frameworks JavaScript
- Compatible con Tailwind CSS

## 🧪 Requisitos para desarrollo

Servidor local simple:

Python:  
python -m http.server

Node.js:  
npx serve

## ⚠️ Disclaimer

Este sistema es una herramienta de análisis informativo.  
No constituye recomendación electoral ni reemplaza el juicio ciudadano.

## © 2026

Grok xAI Intelligence Report  
Dashboard experimental de análisis político
