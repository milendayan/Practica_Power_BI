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
https://www.kaggle.com/datasets/isaac09/age-dataset-life-work-and-death-of-1-22m-people

El dataset contiene información estructurada sobre **1.22 millones de personas famosas o históricamente relevantes** que ya han fallecido, incluyendo datos sobre su vida, profesión y fallecimiento.

Fue construido a partir de información de **Wikidata y Wikipedia en múltiples idiomas**, lo que permite analizar patrones históricos de mortalidad en diferentes contextos sociales y profesionales.

## 🗂 Columnas del dataset

El archivo original contiene 10 columnas, entre ellas: **Id, Name, Gender, Country, Occupation, Birth year, Death year, Manner of death y Age of death**.

Para este proyecto se utilizaron únicamente las siguientes variables necesarias para el análisis:

- Id
- Gender
- Occupation
- Death year
- Manner of death
- Age of death

Aunque el dataset original incluye **1.22 millones de personas**, tras aplicar filtros de calidad y periodo histórico se trabajó con **45,930 registros** correspondientes a personas fallecidas entre **1800 y 2020**, lo que permitió un análisis más consistente y comparable.

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
