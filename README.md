# 🛒 Simulación HMM — Predicción de Intención de Compra en E-commerce

> **Actividad Didáctica 2 — Módulo 2 | Simulación y Modelado de Sistemas**  
> Juan David Calle Correa & Edinson Mena Arroyo  
> Universidad Digital de Antioquia · 2026-02  
> Docente: Julián Andrés Loaiza López

---

## 📌 Descripción

Implementación completa de un **Modelo Oculto de Markov (HMM)** en Python para predecir la intención de usuario en un sitio web de e-commerce a partir de acciones observables (clicks, scrolls, compras).

El modelo infiere tres **estados mentales no observables** a partir de tres **acciones visibles**, simulando sesiones de usuario y generando métricas de conversión, análisis de embudo y recomendaciones de UX.

---

## 🧠 Parámetros del Modelo

### Estados ocultos (S) y Observaciones (O)

| Estados ocultos | Observaciones |
|---|---|
| 👁️ Navegando | Click |
| 🔍 Buscando | Scroll |
| 🛒 Comprando | Compra |

### Probabilidades iniciales (π)

| Estado | Probabilidad |
|---|---|
| Navegando | 0.60 |
| Buscando | 0.30 |
| Comprando | 0.10 |

### Matriz de Transición (A)

| Desde \ Hacia | Navegando | Buscando | Comprando |
|---|---|---|---|
| **Navegando** | 0.50 | 0.40 | 0.10 |
| **Buscando** | 0.30 | 0.50 | 0.20 |
| **Comprando** | 0.20 | 0.30 | 0.50 |

### Matriz de Emisión (B)

| Estado \ Obs. | Click | Scroll | Compra |
|---|---|---|---|
| **Navegando** | 0.60 | 0.35 | 0.05 |
| **Buscando** | 0.50 | 0.40 | 0.10 |
| **Comprando** | 0.20 | 0.30 | 0.50 |

---

## 🚀 Ejecución en Google Colab (recomendado)

1. Abrir [Google Colab](https://colab.research.google.com)
2. `Archivo` → `Abrir cuaderno` → pestaña `GitHub`
3. Pegar la URL de este repositorio
4. Seleccionar `HMM_Ecommerce_FINAL.ipynb`
5. `Entorno de ejecución` → `Ejecutar todo` (`Ctrl+F9`)

---

## 💻 Ejecución local

```bash
git clone https://github.com/[usuario]/hmm-ecommerce-simulation
cd hmm-ecommerce-simulation
pip install -r requirements.txt
jupyter notebook HMM_Ecommerce_FINAL.ipynb
```

**requirements.txt**
```
numpy>=1.24
matplotlib>=3.7
seaborn>=0.12
jupyter>=1.0
```

---

## 📁 Estructura del repositorio

```
hmm-ecommerce-simulation/
│
├── HMM_Ecommerce_FINAL.ipynb      ← Notebook principal (15 secciones)
├── README.md                       ← Este archivo
├── requirements.txt                ← Dependencias
│
├── results/                        ← Gráficas generadas por el notebook
│   ├── heatmap_matrices_HMM.png    ← Heatmaps de A y B
│   ├── sesion_individual_HMM.png   ← Timeline con íconos 👁️🔍🛒
│   ├── funnel_conversion_HMM.png   ← Funnel de conversión
│   ├── resultados_simulacion_HMM.png ← KPIs de 100 sesiones
│   └── funnel_transiciones_HMM.png ← Análisis de embudo
│
└── docs/
    └── Informe_HMM_APA7_FINAL.docx ← Informe completo (normas APA 7)
```

---

## 🏗️ Métodos de la clase `HMM`

| Método | Descripción |
|---|---|
| `__init__(estados, obs_names, pi, A, B)` | Constructor con validación automática (sumas = 1) |
| `simular_sesion(T, semilla)` | Muestreo Monte Carlo de T pasos, semilla configurable |
| `viterbi(obs_seq)` | Decodificación en log-espacio. Complejidad O(N²T) |
| `predecir_conversion(obs_seq, umbral)` | Forward algorithm → P(Comprando\|O). Predicción binaria |
| `calcular_metricas(resultados)` | KPIs agregados sobre N sesiones |
| `generar_recomendaciones(metricas)` | Recomendaciones UX por nivel de urgencia |

---

## 📊 Resultados Destacados (100 sesiones × 40 pasos)

- **Tasa de conversión simulada**: ~45–55% (varía por semilla)
- **Precisión algoritmo Viterbi**: ~65–75%
- **Paso promedio de primera compra**: ~8–15
- **Bigrama más frecuente en compradores**: Scroll → Compra
- **5 visualizaciones** generadas automáticamente

---

## 📋 Checklist de la Rúbrica

| Criterio | Estado |
|---|---|
| ✅ Comprensión conceptual del HMM | Clase HMM con documentación matemática |
| ✅ Formulación y pertinencia del problema | E-commerce con estados ocultos justificados |
| ✅ Matrices π, A, B completas y coherentes | Validación automática en constructor |
| ✅ Simulación ejecutable con resultados | 100 sesiones × 40 pasos, 5 gráficas |
| ✅ Predictor de conversión | Forward algorithm implementado |
| ✅ Recomendaciones de UX | Generadas automáticamente por el modelo |
| ✅ Análisis de embudo (funnel) | Gráfica de funnel + heatmap de diferencias |
| ✅ Patrones compradores vs. no compradores | Tabla comparativa + bigramas |
| ✅ Ejecutable en Google Colab | Sin dependencias externas |

---

## 👥 Autores

**Juan David Calle Correa** · **Edinson Mena Arroyo**  
Ingeniería de Software y Datos · Universidad Digital de Antioquia  
PREICA2601B020049 · 2026-02
