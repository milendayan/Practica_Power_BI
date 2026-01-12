# 📊 Factores que influyen en la edad de fallecimiento de personas famosas

## 📌 Descripción del proyecto

Este proyecto analiza cómo diferentes factores como la **ocupación**, el **género**, el **periodo histórico** y la **causa de muerte** influyen en la **edad de fallecimiento** de personas famosas y figuras históricamente relevantes.

Se desarrolló un **dashboard interactivo en Power BI** utilizando un conjunto de datos real que contiene **1.22 millones de personas**. Para el análisis se trabajó con un subconjunto de **45.930 registros**, correspondiente a personas fallecidas entre los años **1800 y 2020**, lo que permitió obtener resultados comparables y confiables.

El objetivo principal es identificar si existen diferencias significativas en la edad de fallecimiento según distintas variables.

---

## 🎯 Problemática

**¿Existen diferencias significativas en la edad de fallecimiento de personas famosas según su ocupación, género y causa de muerte entre los años 1800 y 2020?**

---

## 🧠 Hipótesis

- La edad promedio de fallecimiento varía según la ocupación.  
- Existen diferencias en la edad de fallecimiento según el género.  
- La edad de fallecimiento ha aumentado con el tiempo.  
- El tipo de ocupación influye en la causa de muerte.

---

## 🗂 Conjunto de datos

**Fuente:** Kaggle – *Age Dataset: Life, Work, and Death of 1.22M People*

Contiene información estructurada sobre más de **1.2 millones de personas famosas o históricamente relevantes**, incluyendo:

- Nombre  
- Género  
- Ocupación  
- País  
- Año de nacimiento  
- Año de fallecimiento  
- Edad al fallecer  
- Causa de muerte  

Para este análisis se utilizaron **45,930 registros** luego de aplicar filtros de calidad.

---

## 🧹 Limpieza y preparación de datos

### 📅 Filtro temporal
- `Death year ≥ 1800`
- `Death year ≤ 2020`

### 📏 Filtro de edad
- `Age of death > 0`
- `Age of death < 120`

### 🧩 Valores nulos
- **Gender** → “Other”  
- **Occupation** → “Other”  
- **Manner of death** → “Unknown”  

---

## 🧱 Columna calculada

```DAX
Periodo =
IF([Death year] < 1900, "1800–1899",
IF([Death year] < 1950, "1900–1949",
IF([Death year] < 2000, "1950–1999", "2000–2020")))
