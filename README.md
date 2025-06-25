# Impacto de la pandemia de COVID‑19 en la mortalidad de la Argentina (2005‑2021)

### 🗒️ Resumen
En este trabajo analizamos **cómo se modificó la mortalidad general en la Argentina durante 2020‑2021** y qué relación guarda con:

1. La cantidad de casos confirmados de COVID‑19.  
2. La campaña de vacunación (dosis aplicadas).  
3. Diferencias geográficas y etarias en el acceso al sistema de salud.  

El objetivo es **cuantificar el exceso de defunciones** respecto de la tendencia histórica (2005‑2019) y explorar patrones provinciales que ayuden a explicar disparidades sanitarias.

---

### 🔍 Hipótesis principales

| Código | Hipótesis | Métrica clave |
|--------|-----------|---------------|
| **H1** | El total de defunciones aumentó de forma estadísticamente significativa en 2020‑2021. | Δ % defunciones vs. promedio 2005‑2019 |
| **H2** | La mortalidad se correlaciona positivamente con la incidencia de casos de COVID‑19. | ρ (casos, defunciones) |
| **H3** | Provincias con mayor cobertura de vacunación presentan menor exceso de mortalidad. | Exceso defunciones ⟂ Dosis / 100 hab. |
| **H4** | Los grupos etarios mayores concentran la mayor variación absoluta de muertes. | Δ defunciones por *grupo_edad* |
| **H5** | Existen provincias con alta letalidad a pesar de vacunación elevada (posibles fallas de acceso a salud). | Letalidad = muertes / casos |

---

### 📦 Fuentes de datos

| Dataset | Descripción | Formato | Fuente |
|---------|-------------|---------|--------|
| **Defunciones 2005‑2021** | Fallecimientos ocurridos y registrados en la República Argentina. | CSV | Ministerio de Salud – Datos Abiertos |
| **Casos COVID‑19** | Registros de casos confirmados diarios. | CSV/ZIP | Ministerio de Salud – CoVid19-Casos |
| **Vacunación COVID‑19 (NOMIVAC)** | Dosis aplicadas por provincia, edad y fecha. | CSV/ZIP | Ministerio de Salud – NOMIVAC |
| **Ocupación de camas** (opcional) | Uso del sistema de salud a lo largo del tiempo. | CSV | Tablero de Gestión COVID‑19 |

> Todas las URLs de descarga están embebidas y automatizadas en el notebook **`Hipotesis_TPO.ipynb`**.

---

### 🛠️ Metodología

1. **Adquisición & limpieza**
     
3. **Transformaciones**  
   * Agrupación por año / provincia / grupo etario.  
   * Cálculo de exceso de mortalidad frente a la media 2005‑2019.  
   * Tablas dinámicas y *pivot* para cruces rápidos.  

4. **Análisis exploratorio**  
   * Tendencias temporales (`lineplot`).  
   * Distribución de causas (`barplot`, top‑N).  
   * Mapas de calor provincia‑edad.  
   * Correlaciones (`heatmap`) entre muertes, casos y dosis.  

5. **Modelado (básico)**  
   * Regresión lineal simple: exceso ~ casos + dosis (ilustrativo).  

6. **Visualización**  
   * `seaborn`, `matplotlib`, uso en Power BI.  
   * Etiquetas envueltas y separadores de miles para legibilidad.  

---

### 📁 Estructura del repositorio

```text
.
├── data/                 # archivos CSV/ZIP originales
├── notebooks/
│   └── Hipotesis_TPO.ipynb
├── src/
│   ├── acquire.py        # utilidades de descarga
│   ├── clean.py          # funciones de limpieza
│   └── viz.py            # helpers de visualización
├── outputs/
│   ├── figs/             # gráficas finales
│   └── tables/           # pivots y CSV derivados
└── README.md             # este documento
