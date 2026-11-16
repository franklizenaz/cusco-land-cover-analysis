# Índices espectrales para detecciónde cambios con LandTrendr

Se utilizarán tres índices con funciones diferenciadas:

| Índice | Función en el estudio |
|---|---|
| **NBR** | Índice principal para detectar perturbaciones y recuperaciones de la vegetación mediante LandTrendr. |
| **NDVI** | Complementar la revisión de cambios en la actividad y presencia de vegetación. |
| **NDMI** | Examinar cambios relacionados con el contenido de humedad de la vegetación. |

### NBR — Normalized Burn Ratio

\[
NBR = \frac{NIR-SWIR2}{NIR+SWIR2}
\]

Utiliza las bandas del infrarrojo cercano y del infrarrojo de onda corta 2.

Será la variable principal de la serie temporal analizada mediante LandTrendr. Las disminuciones importantes del índice se considerarán perturbaciones espectrales candidatas, mientras que sus incrementos podrán representar procesos de recuperación de la señal vegetal.

### NDVI — Normalized Difference Vegetation Index

\[
NDVI = \frac{NIR-RED}{NIR+RED}
\]

Se utilizará como índice complementario para revisar la evolución de la vegetación y contrastar la coherencia de los eventos detectados mediante NBR.

### NDMI — Normalized Difference Moisture Index

\[
NDMI = \frac{NIR-SWIR1}{NIR+SWIR1}
\]

Se utilizará para complementar la interpretación de variaciones relacionadas con la humedad de la vegetación.

**Criterio de aplicación:** LandTrendr se ejecutará inicialmente sobre NBR. NDVI y NDMI servirán como referencias complementarias; no se combinarán automáticamente ni se utilizarán para asignar categorías de cambio.