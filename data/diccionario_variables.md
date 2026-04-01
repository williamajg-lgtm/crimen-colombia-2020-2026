# Diccionario de Variables

## df_eventos.csv

| Variable | Tipo | Descripción |
|---|---|---|
| `idevento` | str | Identificador único del evento (concatenación de variables clave) |
| `fecha` | date | Fecha del evento |
| `anio` | int | Año del evento (2020–2026) |
| `mes` | int | Mes del evento |
| `depto_cod` | str | Código DANE del departamento |
| `mpio_cod` | str | Código DANE del municipio |
| `tipo_delito` | str | Categoría del delito |
| `genero` | str | Género de la víctima |
| `nregistros` | int | Número de registros originales agrupados en el evento |
| `lat` | float | Latitud (georreferenciación DANE) |
| `lon` | float | Longitud (georreferenciación DANE) |
| `cluster` | int | Etiqueta del cluster espacial asignado |

## df_registros_limpios_sample.csv

Muestra de 50.000 registros del nivel micro tras el proceso de limpieza (FASE 1).
Contiene las mismas variables base antes de la agregación por evento.
