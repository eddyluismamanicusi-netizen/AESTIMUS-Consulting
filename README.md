<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24&height=280&section=header&text=AESTIMUS&fontSize=90&fontColor=ffffff&fontAlignY=42&desc=Messaging-Based%20Data%20Integration%20for%20Construction%20Valuation%20Automation&descAlignY=62&descSize=16&descColor=c9d1d9&animation=fadeIn" width="100%"/>

</div>

<div align="center">

[![n8n](https://img.shields.io/badge/n8n-Workflow%20Engine-EA4B71?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io)
[![llama](https://img.shields.io/badge/LLAMA%203.1-Groq%20API-F97316?style=flat-square&logo=meta&logoColor=white)](https://groq.com)
[![revit](https://img.shields.io/badge/Autodesk-Revit%20%2B%20Dynamo-0696D7?style=flat-square&logo=autodesk&logoColor=white)](https://autodesk.com)
[![telegram](https://img.shields.io/badge/Telegram-Bot%20API-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://core.telegram.org/bots)
[![python](https://img.shields.io/badge/Python-Scripts-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![sheets](https://img.shields.io/badge/Google-Sheets%20%2B%20Drive-34A853?style=flat-square&logo=googledrive&logoColor=white)](https://drive.google.com)
[![powerbi](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat-square&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![license](https://img.shields.io/badge/License-CC%20BY%204.0-22C55E?style=flat-square)](LICENSE)

<br/>

**AESTIMUS** es un sistema de integración de datos basado en mensajería que automatiza el flujo de valorizaciones de obra en proyectos de inversión pública en el Perú — integrando captura de campo, modelos BIM, orquestación con IA y generación automática de entregables.

<br/>

[**Resultados**](#-resultados) · [**Arquitectura**](#️-arquitectura) · [**Entregables**](#-entregables-del-sistema) · [**Stack**](#-stack-tecnológico) · [**Equipo**](#-equipo)

<br/>

---

</div>

<br/>

## ¿Qué es AESTIMUS?

En el Perú, la valorización de obra es el instrumento técnico-administrativo mediante el cual se reporta el avance ejecutado y se sustenta el pago al contratista. En la práctica, el proceso concentra una de las mayores fuentes de ineficiencia del sector: el Ingeniero de Producción recopila datos de campo en reportes dispersos, la Oficina Técnica los organiza partida por partida en hojas de cálculo independientes, y cada conciliación entre Residente, Supervisor y Entidad implica múltiples rondas de revisión — generando inconsistencias documentales, retrasos y riesgo real de controversia contractual.

**AESTIMUS** resuelve esta fragmentación.

Es una arquitectura de procesamiento automatizado que integra reportes de campo vía **Telegram**, modelos **BIM**, y **flujos orquestados con IA** en un pipeline continuo y trazable. No opera de forma lineal, sino como un **flujo condicional con puntos de decisión técnica** — arquitectura híbrida entre automatización determinística y sistemas agénticos — que genera automáticamente los entregables de valorización con mínima intervención manual.

```
Telegram (campo) → BOT Aestimus (n8n + LLAMA 3.1) → Google Sheets/Drive → 7 entregables
```

> Publicado en **AI TALENT | Programa de Entrenamiento en IA y Herramientas Digitales para el Sector AEC**
> Ed. No. 01, Abril 2026 · Lima, Perú · Licencia CC BY 4.0

<br/>

---

## 🎯 El Problema que Resolvemos

Las deficiencias en la gestión de **valorizaciones de obra** generan una cadena directa de consecuencias en la inversión pública peruana:

<div align="center">

| Problemática en Valorizaciones | Consecuencia Directa |
|:---|:---:|
| 🔴 Metrados cuantificados sin sustento documentado | Observaciones de Contraloría · Pagos indebidos |
| 🔴 Baja interoperabilidad entre modelo BIM, avance de campo y sistema de pago | Fragmentación · Duplicidad de esfuerzos |
| 🔴 Proceso 100% manual: campo → oficina técnica → supervisor → entidad | 16 horas por ciclo de valorización |
| 🔴 Desalineación entre avance físico y financiero en expedientes | Inconsistencias · Reprocesos · Retrasos |
| 🔴 Limitada trazabilidad entre fuentes y entregables | Controversias contractuales · Arbitrajes |

</div>

> Al cierre de 2024 existen **2,476 obras públicas paralizadas** con más de **S/ 43,118 millones** inmovilizados en el Perú. Una causa estructural recurrente: la deficiente trazabilidad del control físico-financiero en etapa de ejecución, que desemboca en controversias y arbitrajes.

<br/>

---

## 🏗️ Arquitectura

El sistema no opera como una secuencia lineal, sino como un **flujo condicional con puntos de decisión técnica** — arquitectura híbrida entre automatización determinística y sistemas agénticos. Se organiza en tres capas articuladas mediante **bases de datos intermedias (L0 → L1 → L2)** y almacenamiento centralizado en **Google Drive**.

<div align="center">

![Arquitectura General del Sistema AESTIMUS](arquitectura_aestimus.png)

*Figura 1. Arquitectura General del Sistema AESTIMUS · Fuente: AESTIMUS Consulting © 2026*

</div>

<br/>

> ⚠️ **Para que la imagen aparezca:** sube el archivo `arquitectura_aestimus.png` a la **raíz** de tu repositorio en GitHub.

<br/>

---

## 📦 Entregables del Sistema

El sistema genera automáticamente **7 entregables técnicos estandarizados** por cada valorización mensual, listos para presentación ante la entidad y registro en el SEACE:

<div align="center">

| Cód. | Entregable | Descripción Técnica | Formatos |
|:---:|:---|:---|:---:|
| `A` | **Memoria Descriptiva Valorizada** | Documento narrativo que describe y sustenta los trabajos ejecutados | `.docx` `.pdf` |
| `B` | **Metrados Realmente Ejecutados** | Cuantificación detallada de partidas ejecutadas en el período | `.xlsx` `.pdf` |
| `C` | **Valorización Mensual** | Cálculo económico del avance de obra con precios unitarios contractuales | `.xlsx` `.pdf` |
| `D` | **Control de Obra — Curva S** | Análisis del avance físico-financiero vs. programado acumulado | `.xlsx` `.pdf` |
| `E` | **Panel Fotográfico** | Registro visual estructurado del avance en campo por partida | `.docx` `.pdf` |
| `F` | **Modelos BIM y Planos de Valorización** | Representación digital del estado real de obra y planos técnicos | `.rvt` `.pdf` `.dwg` |
| `G` | **Dashboard y Análisis Ejecutivo** | Visualización de indicadores y síntesis para toma de decisiones | `.pbix` `.pdf` |

</div>

<br/>

---

## 📊 Resultados

> Proyecto piloto **I.E. Fe y Alegría N.° 23** · Villa María del Triunfo, Lima · S/ 13,113,956.86 · 334 días calendario
> Método Tradicional (línea base histórica) vs. Sistema AESTIMUS (Valorización N.° 08 — primera ejecución completa)

<br/>

<div align="center">

<img src="https://quickchart.io/chart?c=%7B%22type%22%3A%22bar%22%2C%22data%22%3A%7B%22labels%22%3A%5B%22TP%3A%20Tiempo%22%2C%22IIM%3A%20Interv.%20Manual%22%2C%22ICD%3A%20Consistencia%22%2C%22COV%3A%20Costo%22%5D%2C%22datasets%22%3A%5B%7B%22label%22%3A%22Metodo%20Tradicional%22%2C%22data%22%3A%5B100%2C100%2C75%2C100%5D%2C%22backgroundColor%22%3A%22rgba%28239%2C68%2C68%2C0.85%29%22%2C%22borderColor%22%3A%22rgba%28239%2C68%2C68%2C1%29%22%2C%22borderWidth%22%3A2%7D%2C%7B%22label%22%3A%22Sistema%20AESTIMUS%22%2C%22data%22%3A%5B50%2C23.3%2C97%2C41.4%5D%2C%22backgroundColor%22%3A%22rgba%2888%2C166%2C255%2C0.85%29%22%2C%22borderColor%22%3A%22rgba%2888%2C166%2C255%2C1%29%22%2C%22borderWidth%22%3A2%7D%5D%7D%2C%22options%22%3A%7B%22legend%22%3A%7B%22labels%22%3A%7B%22fontColor%22%3A%22%23c9d1d9%22%2C%22fontSize%22%3A14%2C%22padding%22%3A20%7D%7D%2C%22scales%22%3A%7B%22xAxes%22%3A%5B%7B%22ticks%22%3A%7B%22fontColor%22%3A%22%23c9d1d9%22%2C%22fontSize%22%3A13%7D%2C%22gridLines%22%3A%7B%22color%22%3A%22rgba%28255%2C255%2C255%2C0.05%29%22%7D%7D%5D%2C%22yAxes%22%3A%5B%7B%22ticks%22%3A%7B%22fontColor%22%3A%22%23c9d1d9%22%2C%22beginAtZero%22%3Atrue%2C%22max%22%3A115%2C%22fontSize%22%3A12%7D%2C%22scaleLabel%22%3A%7B%22display%22%3Atrue%2C%22labelString%22%3A%22Valor%20normalizado%20%5Cu2014%20Tradicional%3D100%20%7C%20ICD%3Dvalor%20absoluto%20%25%22%2C%22fontColor%22%3A%22%238b949e%22%2C%22fontSize%22%3A12%7D%2C%22gridLines%22%3A%7B%22color%22%3A%22rgba%28255%2C255%2C255%2C0.07%29%22%7D%7D%5D%7D%2C%22title%22%3A%7B%22display%22%3Atrue%2C%22text%22%3A%22Metodo%20Tradicional%20vs%20Sistema%20AESTIMUS%20%5Cu2014%20Indicadores%20de%20Desempeno%22%2C%22fontColor%22%3A%22%23ffffff%22%2C%22fontSize%22%3A16%2C%22padding%22%3A20%7D%7D%7D&backgroundColor=%230d1117&width=900&height=460" alt="Resultados AESTIMUS vs Método Tradicional" width="900"/>

</div>

<br/>

<div align="center">

**📌 Indicadores Principales**

| Indicador | Tradicional | AESTIMUS | Δ Variación |
|:---|:---:|:---:|:---:|
| ⏱️ **(TP)** Tiempo de Procesamiento | 16 h | 8 h | **↓ 50.0 %** |
| 🖐️ **(IIM)** Índice de Intervención Manual | 90 % | 21 % | **↓ 76.7 %** |
| 📋 **(ICD)** Índice de Consistencia Documental | 75 % | 97 % | **↑ +22 p.p.** |
| 💰 **(COV)** Costo Operativo de Valorización | S/. 1,900 | S/. 787.52 | **↓ 58.6 %** |

**📌 Indicadores Complementarios**

| Indicador | Tradicional | AESTIMUS |
|:---|:---:|:---:|
| 👥 **(NP)** Profesionales involucrados | 5 personas | 3 personas |
| 🤖 **(NA)** Nivel de Automatización | Básico e Ineficiente `(1/4)` | Alto y Eficiente `(3/4)` |

*pp = puntos porcentuales · Gráfico normalizado: Tradicional = 100 en TP, IIM y COV · ICD muestra valor absoluto*

</div>

<br/>

---

## 💻 Stack Tecnológico

<div align="center">

| | Tecnología | Rol en el Sistema |
|:---:|:---|:---|
| 📱 | **Telegram Bot API** | Interfaz de captura — 4 tipos de mensajes estructurados desde campo (1A, 2A, 1B, 2B) |
| ⚡ | **n8n** | Motor del BOT Aestimus — orquestación del pipeline ETL completo |
| 🤖 | **LLAMA 3.1 vía Groq** | Clasificación semántica de mensajes · Generación de Memoria Descriptiva · Panel Fotográfico |
| 🏗️ | **Autodesk Revit** | Modelo BIM con parámetros AC_ para control y valorización de obra |
| 🔁 | **Dynamo** | Scripts de asignación y extracción automática de parámetros BIM a Excel |
| 🐍 | **Python** | Transformación de datos y asignación masiva de parámetros en elementos Revit |
| 📊 | **Google Sheets** | Capas de datos L0 · L1 · L2 — consolidación y plantillas de cálculo automatizadas |
| ☁️ | **Google Drive** | Almacenamiento cloud centralizado — backbone de disponibilidad y trazabilidad |
| 📈 | **Power BI** | Dashboard ejecutivo de indicadores físico-financieros (`.pbix`) |

</div>

<br/>

---

## 📈 Actividad

<div align="center">

[![GitHub Streak](https://streak-stats.demolab.com?user=eddyluismamanicusi-netizen&theme=github-dark-blue&hide_border=true&border_radius=8&locale=es&date_format=j%20M%5B%20Y%5D&ring=58a6ff&fire=ff6b35&currStreakLabel=58a6ff)](https://git.io/streak-stats)

<br/>

<img src="https://github-readme-stats.vercel.app/api?username=eddyluismamanicusi-netizen&show_icons=true&theme=github_dark&hide_border=true&border_radius=8&icon_color=58a6ff&title_color=58a6ff" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=eddyluismamanicusi-netizen&layout=compact&theme=github_dark&hide_border=true&border_radius=8&title_color=58a6ff" height="165"/>

</div>

<br/>

---

## 👥 Equipo

<div align="center">

| Integrante | Rol | Universidad |
|:---|:---|:---:|
| **Alexander Daniel Cristobal Taquire** | Jefe de Proyecto — Gestión de Información de Valorizaciones | Universidad Privada del Norte |
| **Yasser Nasser Ladera Gavilan** | Jefe de Automatización e Inteligencia Artificial | Universidad Peruana de Ciencias Aplicadas |
| **Milagros Raquel Gómez M.** | Jefa BIM — Coordinación e Integración de Información | Pontificia Universidad Católica del Perú |
| **Eddy Luis Mamani Cusi** | Analista de Optimización — Procesos con IA | Universidad Peruana Unión |

<br/>

[![GitHub](https://img.shields.io/badge/GitHub-eddyluismamanicusi--netizen-181717?style=for-the-badge&logo=github)](https://github.com/eddyluismamanicusi-netizen)

</div>

<br/>

---

## 📄 Licencia

Distribuido bajo la licencia **Creative Commons Attribution 4.0 International (CC BY 4.0)**.
Permite compartir y adaptar el material para cualquier propósito, con reconocimiento de autoría.
Ver [`LICENSE`](LICENSE) para más información.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24&height=140&section=footer&animation=fadeIn" width="100%"/>

**AESTIMUS** · Construido en Perú 🇵🇪 · © 2026 AESTIMUS Consulting S.A.C.

*Publicado en AI TALENT — Programa de Entrenamiento en IA y Herramientas Digitales para el Sector AEC*

[![Visitors](https://visitor-badge.laobi.icu/badge?page_id=eddyluismamanicusi-netizen.AESTIMUS-Consulting&left_color=161b22&right_color=58a6ff&left_text=visitors)](https://github.com/eddyluismamanicusi-netizen/AESTIMUS-Consulting)

</div>


