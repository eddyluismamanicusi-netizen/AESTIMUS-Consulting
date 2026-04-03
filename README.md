<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24&height=280&section=header&text=AESTIMUS&fontSize=90&fontColor=ffffff&fontAlignY=42&desc=Intelligent%20Construction%20Valuation%20Automation&descAlignY=62&descSize=18&descColor=c9d1d9&animation=fadeIn" width="100%"/>

</div>

<div align="center">

[![made-with-n8n](https://img.shields.io/badge/n8n-Workflow%20Engine-EA4B71?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io)
[![llama](https://img.shields.io/badge/LLAMA%203.1-Groq%20API-F97316?style=flat-square&logo=meta&logoColor=white)](https://groq.com)
[![revit](https://img.shields.io/badge/Autodesk-Revit%20%2B%20Dynamo-0696D7?style=flat-square&logo=autodesk&logoColor=white)](https://autodesk.com)
[![telegram](https://img.shields.io/badge/Telegram-Bot%20API-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://core.telegram.org/bots)
[![status](https://img.shields.io/badge/Status-Production%20Ready-22C55E?style=flat-square&logo=statuspage&logoColor=white)](https://github.com/eddyluismamanicusi-netizen/AESTIMUS-Consulting)
[![license](https://img.shields.io/badge/License-MIT-8B949E?style=flat-square)](LICENSE)

<br/>

**AESTIMUS** es un sistema de automatización inteligente que transforma el proceso de valorización de obras públicas en el Perú — de 4 días de trabajo manual a 1 día completamente automatizado.

<br/>

[**Ver Resultados**](#-resultados) · [**Arquitectura**](#️-arquitectura) · [**Entregables**](#-entregables-del-sistema) · [**Stack**](#-tecnologías)

<br/>

---

</div>

<br/>

## ¿Qué es AESTIMUS?

El proceso de valorización de obras en el Perú concentra una de las mayores fuentes de ineficiencia en la gestión de inversión pública. Metrados cuantificados manualmente, hojas de cálculo desconectadas, múltiples rondas de revisión entre el residente, supervisor y entidad — y al final: retrasos, inconsistencias y riesgo de controversia contractual.

**AESTIMUS** elimina ese ciclo.

Es un sistema de integración de datos basado en mensajería que captura el avance de obra directamente desde campo vía Telegram, lo procesa con inteligencia artificial y genera automáticamente los **9 entregables técnicos** de una valorización — sin intervención manual en el flujo.

```
Ingeniero en campo → Telegram → IA → n8n + BIM → 9 entregables listos
```

> Desarrollado y validado por **AESTIMUS Consulting** en el contexto de proyectos de inversión pública peruanos.

<br/>

---

## 🎯 El Problema que Resolvemos

<div align="center">

| Situación actual en el Perú | Impacto |
|:---|:---:|
| 🔴 2,476 obras públicas paralizadas al cierre de 2024 | **S/ 43,118 M** inmovilizados |
| 🔴 Plazos extendidos hasta un 524.2% del plazo original | Controversias y arbitrajes |
| 🔴 Valorizaciones formuladas sin sustento de metrados | Observaciones de Contraloría |
| 🔴 Proceso 100% manual entre campo, oficina técnica y supervisión | 4 días por valorización |

</div>

La raíz del problema es estructural: **no existe interoperabilidad** entre el modelo BIM del proyecto, el seguimiento de avance en campo y el sistema de gestión de pagos. AESTIMUS cierra esa brecha.

<br/>

---

## 🏗️ Arquitectura

```mermaid
flowchart TD
    A(["👷 Ingeniero de Producción\n(Campo)"]) --> B

    subgraph INPUT ["📥  CAPA DE ENTRADA"]
        B["📱 Telegram Bot\nMensaje de avance por partida"]
        B --> C["🤖 LLAMA 3.1 vía Groq\nClasificación semántica y validación"]
    end

    C --> D

    subgraph PROCESS ["⚙️  CAPA DE PROCESAMIENTO — n8n"]
        D["🔀 n8n\nMotor de Orquestación"]
        D --> E["🏗️ Dynamo + Revit\nExtracción de metrados BIM"]
        D --> F["📊 Google Sheets\nValidación y consolidación"]
        D --> G["⚠️ Control de errores\ny excepciones"]
        E --> H["🔄 ETL Pipeline\nTransformación de datos"]
        F --> H
        G --> H
    end

    H --> I

    subgraph OUTPUT ["📤  CAPA DE SALIDA"]
        I["📦 Generador de Entregables"]
        I --> J["📐 Metrados\n💰 Valorización\n📝 Informes"]
        I --> K["📸 Panel Fotográfico\n📊 Dashboard\n📅 Cronograma"]
        I --> L["🗂️ Expediente SEACE\n⚠️ Observaciones\n📈 KPIs"]
    end

    style INPUT fill:#0d1117,stroke:#58a6ff,stroke-width:2px,color:#c9d1d9
    style PROCESS fill:#0d1117,stroke:#ea4b71,stroke-width:2px,color:#c9d1d9
    style OUTPUT fill:#0d1117,stroke:#22c55e,stroke-width:2px,color:#c9d1d9
    style A fill:#161b22,stroke:#58a6ff,color:#ffffff
    style B fill:#161b22,stroke:#26a5e4,color:#c9d1d9
    style C fill:#161b22,stroke:#f97316,color:#c9d1d9
    style D fill:#161b22,stroke:#ea4b71,color:#c9d1d9
    style E fill:#161b22,stroke:#0696d7,color:#c9d1d9
    style F fill:#161b22,stroke:#34a853,color:#c9d1d9
    style G fill:#161b22,stroke:#f59e0b,color:#c9d1d9
    style H fill:#161b22,stroke:#ea4b71,color:#c9d1d9
    style I fill:#161b22,stroke:#22c55e,color:#c9d1d9
    style J fill:#161b22,stroke:#22c55e,color:#c9d1d9
    style K fill:#161b22,stroke:#22c55e,color:#c9d1d9
    style L fill:#161b22,stroke:#22c55e,color:#c9d1d9
```

<br/>

---

## 📦 Entregables del Sistema

Cada ciclo de valorización produce automáticamente **9 documentos técnicos estandarizados**, listos para presentación ante la entidad y registro en el SEACE:

<div align="center">

| # | Entregable | Descripción |
|:---:|:---|:---|
| `01` | **Planilla de Metrados** | Cómputo métrico automático por partida desde modelo BIM |
| `02` | **Valorización de Obra** | Aplicación de precios unitarios según contrato |
| `03` | **Informe Descriptivo** | Narrativa técnica del avance ejecutado en el período |
| `04` | **Panel Fotográfico** | Registro gráfico organizado por partida ejecutada |
| `05` | **Dashboard Ejecutivo** | Indicadores de avance físico-financiero consolidados |
| `06` | **Control de Cronograma** | Comparativo programado vs. real del período |
| `07` | **Expediente de Valorización** | Consolidación documental para registro SEACE |
| `08` | **Reporte de Observaciones** | Inconsistencias detectadas con trazabilidad completa |
| `09` | **Informe de KPIs** | Indicadores de desempeño operativo del período |

</div>

<br/>

---

## 📊 Resultados

> Validado en el proyecto **I.E. Fe y Alegría N.º 23** · AESTIMUS Consulting
> Comparación directa: flujo manual (Feb 2026) vs. AESTIMUS automatizado (Mar 2026)

<br/>

<div align="center">

<!-- 
  Gráfico normalizado: Método Manual = 100% (baseline) en todos los indicadores de reducción.
  AESTIMUS muestra el % que representa respecto al baseline manual.
  Tiempo:         1/4   dias  = 25%   (↓ 75%)
  Errores:        2/7         = 28.6% (↓ 71.4%)
  Intervenciones: 19/94       = 20.2% (↓ 79.8%)
  Consistencia:   58% → 96%  (único indicador que sube — se muestra valor absoluto)
  Costo:          800/1600    = 50%   (↓ 50%)
-->

<img src="https://quickchart.io/chart?c=%7B%22type%22%3A%22bar%22%2C%22data%22%3A%7B%22labels%22%3A%5B%22Tiempo%20%28dias%29%22%2C%22Errores%22%2C%22Intervenciones%22%2C%22Consistencia%22%2C%22Costo%22%5D%2C%22datasets%22%3A%5B%7B%22label%22%3A%22Metodo%20Manual%22%2C%22data%22%3A%5B100%2C100%2C100%2C58%2C100%5D%2C%22backgroundColor%22%3A%22rgba%28239%2C68%2C68%2C0.85%29%22%2C%22borderColor%22%3A%22rgba%28239%2C68%2C68%2C1%29%22%2C%22borderWidth%22%3A2%7D%2C%7B%22label%22%3A%22AESTIMUS%22%2C%22data%22%3A%5B25%2C28.6%2C20.2%2C96%2C50%5D%2C%22backgroundColor%22%3A%22rgba%2888%2C166%2C255%2C0.85%29%22%2C%22borderColor%22%3A%22rgba%2888%2C166%2C255%2C1%29%22%2C%22borderWidth%22%3A2%7D%5D%7D%2C%22options%22%3A%7B%22plugins%22%3A%7B%22legend%22%3A%7B%22labels%22%3A%7B%22fontColor%22%3A%22%23c9d1d9%22%2C%22fontSize%22%3A13%2C%22padding%22%3A20%7D%7D%7D%2C%22scales%22%3A%7B%22xAxes%22%3A%5B%7B%22ticks%22%3A%7B%22fontColor%22%3A%22%23c9d1d9%22%2C%22fontSize%22%3A13%7D%2C%22gridLines%22%3A%7B%22color%22%3A%22rgba%28255%2C255%2C255%2C0.05%29%22%7D%7D%5D%2C%22yAxes%22%3A%5B%7B%22ticks%22%3A%7B%22fontColor%22%3A%22%23c9d1d9%22%2C%22beginAtZero%22%3Atrue%2C%22max%22%3A115%2C%22fontSize%22%3A12%7D%2C%22scaleLabel%22%3A%7B%22display%22%3Atrue%2C%22labelString%22%3A%22%25%20vs%20baseline%20manual%20%28100%25%29%22%2C%22fontColor%22%3A%22%238b949e%22%2C%22fontSize%22%3A12%7D%2C%22gridLines%22%3A%7B%22color%22%3A%22rgba%28255%2C255%2C255%2C0.08%29%22%7D%7D%5D%7D%2C%22title%22%3A%7B%22display%22%3Atrue%2C%22text%22%3A%22Manual%20vs%20AESTIMUS%20%5Cu2014%20Indicadores%20normalizados%20%28baseline%20manual%20%3D%20100%25%29%22%2C%22fontColor%22%3A%22%23ffffff%22%2C%22fontSize%22%3A15%2C%22padding%22%3A20%7D%7D%7D&backgroundColor=%230d1117&width=860&height=440" alt="Comparativo normalizado Manual vs AESTIMUS" width="860"/>

</div>

<br/>

<div align="center">

| Indicador | Método Manual | AESTIMUS | Reducción |
|:---|:---:|:---:|:---:|
| ⏱️ Tiempo de procesamiento | 4 días hábiles | 1 día hábil | **↓ 75.0 %** |
| ❌ Errores e inconsistencias | 7 observaciones | 2 observaciones | **↓ 71.4 %** |
| 🖐️ Intervenciones manuales | 94 por valorización | 19 por valorización | **↓ 79.8 %** |
| 📋 Consistencia documental | 58 % | 96 % | **↑ 38 p.p.** |
| 💰 Costo operativo | S/ 1,600 | S/ 800 | **↓ 50.0 %** |

</div>

<br/>

---

## 💻 Tecnologías

<div align="center">

|  | Tecnología | Función |
|:---:|:---|:---|
| 📱 | **Telegram Bot API** | Captura estructurada de avance desde campo |
| 🤖 | **LLAMA 3.1 vía Groq** | Clasificación semántica y validación de mensajes |
| ⚙️ | **n8n** | Orquestación de flujos ETL y automatización de salidas |
| 🏗️ | **Autodesk Revit** | Modelo BIM fuente de metrados y geometría |
| 🔁 | **Dynamo** | Scripts de extracción automática desde modelos BIM |
| 📊 | **Google Sheets** | Capa de datos y consolidación de información |

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

| Investigador | Universidad |
|:---|:---:|
| Alexander Cristobal | Universidad Privada del Norte |
| Yasser Ladera | Universidad Peruana de Ciencias Aplicadas |
| Milagros Gómez | Pontificia Universidad Católica del Perú |
| Eddy Mamani | Universidad Peruana Unión |

<br/>

[![GitHub](https://img.shields.io/badge/GitHub-eddyluismamanicusi-netizen-181717?style=for-the-badge&logo=github)](https://github.com/eddyluismamanicusi-netizen)

</div>

<br/>

---

## 📄 Licencia

Distribuido bajo la licencia **MIT**. Ver [`LICENSE`](LICENSE) para más información.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24&height=140&section=footer&animation=fadeIn" width="100%"/>

**AESTIMUS** · Construido en Perú 🇵🇪 · © 2026 AESTIMUS Consulting

[![Visitors](https://visitor-badge.laobi.icu/badge?page_id=eddyluismamanicusi-netizen.AESTIMUS-Consulting&left_color=161b22&right_color=58a6ff&left_text=visitors)](https://github.com/eddyluismamanicusi-netizen/AESTIMUS-Consulting)

</div>
