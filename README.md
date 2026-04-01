# Pipeline de Criminalidad en Colombia (2020–2026)

> Este repositorio contiene el pipeline de procesamiento y análisis de datos de criminalidad en Colombia para el periodo 2020–2026, incluyendo limpieza, agregación de eventos y análisis espacial.

---

## Descripción del problema

La disponibilidad de registros criminales a gran escala en Colombia no garantiza, por sí sola, una interpretación territorial consistente de la criminalidad, debido a problemas como heterogeneidad, duplicidad y débil estructuración espacial de los datos.

Este proyecto analiza el papel de la **limpieza, agregación y georreferenciación** de la información en la identificación de patrones territoriales de criminalidad, trabajando con bases oficiales del periodo 2020–2026.

### Proceso metodológico
- Estandarización de variables (nombres, tipos y codificación)
- Definición de una unidad de evento
- Tratamiento de duplicidades y valores atípicos
- Vinculación espacial mediante códigos geográficos oficiales (DANE)
- Clustering espacial para identificación de patrones territoriales

---

## Estructura del repositorio

```
crimen-colombia-2020-2026/
├─ data/
│  ├─ df_eventos.csv                     # Base agregada por evento (nivel analítico)
│  ├─ df_registros_limpios_sample.csv    # Muestra de registros limpios (50k filas)
│  └─ diccionario_variables.md           # Descripción de variables
├─ notebooks/
│  ├─ 01_FASE1_limpieza.ipynb
│  └─ 02_FASE2_construccion_eventos_geoespacial_clustering.ipynb
├─ README.md
├─ .gitignore
└─ requirements.txt
```

---

## Datos

| Archivo | Descripción | Nivel |
|---|---|---|
| `df_eventos.csv` | Base agregada: 1 fila ≈ 1 evento, con `nregistros`, variables geográficas y temporales | Evento |
| `df_registros_limpios_sample.csv` | Muestra ilustrativa de registros tras la limpieza | Micro |

> **Nota:** Por razones de tamaño y confidencialidad, la base completa (~6.7M registros) **no** se incluye en este repositorio.

---

## Notebooks

### `01_FASE1_limpieza.ipynb`
Integración de archivos anuales (2020–2026), estandarización de variables, creación de la variable `anio` y consolidación de la base única de registros (~6.7M).

Incluye:
- Diagnóstico de nulos y duplicados
- Resumen descriptivo inicial
- Exportación de `df_registros_limpios`

### `02_FASE2_construccion_eventos_geoespacial_clustering.ipynb`
Construcción de la unidad de evento (`idevento`), agregación de registros para formar `df_eventos`, tratamiento de valores atípicos por percentil, integración con códigos DANE y clustering espacial.

Incluye:
- Georreferenciación por códigos municipales DANE
- Análisis de conglomerados espaciales
- Caracterización de clusters por tipo de delito, género e intensidad territorial

---

## Cómo reproducir

```bash
# 1. Clonar el repositorio
git clone https://github.com/williamajg-lgtm/crimen-colombia-2020-2026.git
cd crimen-colombia-2020-2026

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Ejecutar los notebooks en orden desde la carpeta notebooks/
```

Asegúrate de mantener la carpeta `data/` en la ruta relativa estándar.

---

## Dependencias principales

```
pandas
numpy
matplotlib
seaborn
scikit-learn
geopandas
contextily
```

---

## Consideraciones metodológicas

La organización y depuración de los datos condiciona directamente la identificación de concentraciones espaciales y la interpretación de los patrones territoriales de criminalidad.

El análisis geográfico de la criminalidad no es solo una cuestión de localización, sino también de **construcción metodológica de la información**: limpieza, definición de eventos y georreferenciamiento.

---

## Autor

**williamajg-lgtm** — Colombia, 2026

---

## Datos

El dataset completo (`df_eventos.csv`, ~6.7M registros) supera el límite de carga de GitHub (25 MB).
Puede acceder al archivo completo en Google Drive:

📂 [Descargar df_eventos.csv (Google Drive)](https://drive.google.com/file/d/1cICJ-nX-6XXUPrrDMtK2hFrdUqqnYINH/view?usp=sharing)

Los archivos incluidos en este repositorio (`data/`) son:
- `CODDANE.xlsx` — tabla de georreferenciación con códigos DANE, latitud y longitud por municipio
