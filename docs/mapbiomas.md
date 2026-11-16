# MapBiomas Perú: Uso para el análisis de cambios entre bosques y áreas agropecuarias

**Área de estudio:** provincia de Cusco  
**Fuente:** MapBiomas Perú – Cobertura y Uso del Suelo, Colección 4  
**Periodo de análisis:** 2013–2025  
**Objetivo:** identificar y cuantificar cambios entre coberturas boscosas y áreas agropecuarias.

---

## 1. ¿Qué es MapBiomas y qué buscamos obtener?

MapBiomas Perú publica mapas anuales de **cobertura y uso del suelo** elaborados a partir de imágenes satelitales **Landsat**. La *Colección 4* comprende el periodo 1985–2025 y tiene una resolución espacial de 30 m.

Cada píxel del mapa contiene un código que representa la cobertura o uso que MapBiomas le asignó en un año determinado. Al comparar los mapas de distintos años podemos identificar cambios de clase.

En esta investigación utilizaremos MapBiomas para:

1. Identificar las coberturas boscosas y agropecuarias presentes en la provincia.
2. Calcular la superficie que ocupa cada clase entre 2013 y 2025.
3. Identificar las áreas que pasan de bosque a uso agropecuario y, también, las transiciones inversas.
4. Localizar espacialmente esas transiciones para orientar el análisis posterior con imágenes Landsat.

> **Importante:** MapBiomas registra cambios entre categorías de cobertura y uso. No mide por sí solo la degradación interna de un bosque ni demuestra la causa del cambio. Las transiciones deben interpretarse como cambios cartográficos de clase y, cuando sea necesario, verificarse con imágenes de referencia independientes.

---

## 2. Primero: entender las clases que realmente nos interesan

La leyenda de la Colección 4 está organizada jerárquicamente. Los códigos de nivel superior agrupan clases; para el análisis píxel a píxel se utilizan los códigos de las clases específicas.

### 2.1 Clases boscosas

| Código | Clase oficial | Interpretación para el estudio |
|---:|---|---|
| 3 | Bosque | Cobertura boscosa natural |
| 4 | Bosque seco | Cobertura boscosa natural de ambientes secos |
| 6 | Bosque inundable | Cobertura boscosa natural asociada a inundación |
| 9 | Plantación forestal | Cobertura arbórea plantada; es antrópica, no debe sumarse automáticamente al bosque natural |

### 2.2 Clases agropecuarias

| Código | Clase oficial | Qué representa |
|---:|---|---|
| 21 | Mosaico agropecuario | Puede incluir ganadería, cereales, tubérculos y hortalizas en valles interandinos. |
| 15 | Pasto (beta) | Puede incluir pastos naturales altoandinos y pasturas cultivadas. |
| 40 | Arroz (beta) | Cultivo de arroz; Mapbiomas no reconoce esta clase dentro de la Región Cusco |
| 35 | Palma aceitera | Cultivo de palma; Mapbiomas no reconoce esta clase dentro de la Región Cusco |

### 2.3 Otras clases que conviene reconocer

| Código | Clase | Por qué tenerla presente |
|---:|---|---|
| 12 | Formación herbácea | Cobertura herbácea natural; en los Andes se asocia al pajonal.|
| 66 | Matorral y otros arbustales | Cobertura natural no boscosa; puede aparecer como transición desde o hacia bosque. |
| 82 | Herbazal inundable altoandino | La leyenda lo asocia a bofedales; no debe confundirse con pajonal ni con área agropecuaria. |
| 24 | Infraestructura urbana | Permite identificar conversión a uso urbano. |
| 30 | Minería | Permite identificar conversión asociada a actividad minera. |
| 33 | Río, lago u océano | Cuerpo de agua. |
| 34 | Glaciar | Cobertura glaciar. |
| 92 | Superficie rocosa | Cobertura natural sin vegetación. |

---

## 3. Diagnóstico exploratorio del departamento de Cusco

Las estadísticas departamentales permiten caracterizar la distribución general de las coberturas en Cusco. Los valores de 2013 y 2025 se presentan como referencia regional y no representan la superficie de la provincia de Cusco.

Para obtener resultados provinciales, las bandas anuales de MapBiomas se procesan en Google Earth Engine (GEE) utilizando el límite de la provincia como área de análisis. Este procedimiento permite calcular superficies y transiciones dentro del polígono provincial, independientemente del nivel de agregación disponible en la plataforma web.

| Clase | 2013 (ha) | 2025 (ha) | Variación (ha) |
|---|---:|---:|---:|
| Bosque | 3,315,707 | 3,300,925 | -14,782 |
| Formación herbácea | 2,348,710 | 2,290,426 | -58,284 |
| Mosaico agropecuario | 473,185 | 499,907 | +26,722 |
| Matorral y otros arbustales | 369,125 | 360,800 | -8,325 |
| Superficie rocosa | 211,272 | 220,449 | +9,177 |
| Otra área natural sin vegetación | 107,020 | 106,357 | -663 |
| Bosque inundable | 84,478 | 77,498 | -6,980 |
| Herbazal inundable altoandino | 71,781 | 67,682 | -4,099 |
| Río, lago u océano | 58,346 | 61,941 | +3,595 |
| Pasto (beta) | 54,038 | 107,695 | +53,657 |
| Glaciar | 40,631 | 31,903 | -8,728 |
| Bosque seco | 22,876 | 23,147 | +271 |
| Otra área antrópica sin vegetación | 9,783 | 13,255 | +3,472 |
| Infraestructura urbana | 9,316 | 12,603 | +3,287 |
| Playa | 15,203 | 12,183 | -3,020 |
| Plantación forestal | 6,970 | 7,183 | +213 |
| Minería | 1,967 | 6,454 | +4,487 |
| No observado | 21 | 22 | +1 |

*Superficies reportadas para el departamento de Cusco. La variación corresponde a la diferencia entre 2025 y 2013.*

Como lectura inicial, el bosque (clase 3) disminuye en 14,782 ha; el bosque inundable (6) disminuye en 6,980 ha; y el bosque seco (4) aumenta en 271 ha. En conjunto, estas tres clases pasan de 3,423,061 ha a 3,401,570 ha, una disminución neta de 21,491 ha.

El mosaico agropecuario (21) aumenta en 26,722 ha y el pasto (15) en 53,657 ha. Sin embargo, la clase 15 requiere una interpretación cuidadosa y la clase 21 combina distintos usos agropecuarios. Estos aumentos **no demuestran que la superficie adicional provenga de la pérdida de bosque**.

### Ocupación territorial

La ocupación expresa la proporción de superficie que representa cada clase respecto al total clasificado en el territorio y año correspondiente. Considerando las clases con superficie reportada, el total clasificado es aproximadamente 7,191,471 ha en 2013 y 7,186,771 ha en 2025.

| Grupo | 2013 | 2025 |
|---|---:|---:|
| Bosque natural (3 + 4 + 6) | 47.60 % | 47.33 % |
| Formación herbácea (12) | 32.66 % | 31.87 % |
| Mosaico agropecuario (21) | 6.58 % | 6.96 % |
| Pasto (15) | 0.75 % | 1.50 % |
| Mosaico agropecuario + pasto (21 + 15) | 7.33 % | 8.45 % |
| Matorral y otros arbustales (66) | 5.13 % | 5.02 % |

*Porcentajes aproximados calculados respecto a la superficie total clasificada en el departamento para cada año. No representan porcentajes provinciales ni miden directamente las transiciones entre clases.*

Estos resultados describen la distribución departamental y sirven como contexto del estudio. Las superficies y porcentajes provinciales se calcularán utilizando exclusivamente el área de interés (AOI) definida para la provincia de Cusco.

---

## 4. Limitaciones que debemos considerar

- MapBiomas tiene resolución de 30 m; no identifica con precisión elementos menores que esa escala.
- La clase 21 agrupa agricultura y pastos; no permite separar ambos usos de manera directa.
- La clase 15 es una categoría beta y debe revisarse antes de usarla como indicador principal.
- Las plantaciones forestales (clase 9) son antrópicas y deben diferenciarse del bosque natural.
- Los cambios de clase pueden incluir errores de clasificación. Revisar las transiciones es necesario antes de atribuirles un significado territorial.
- MapBiomas no sustituye la validación independiente del estudio.

---

## 5. Fuentes oficiales

1. **MapBiomas Perú – Cobertura y Uso del Suelo, Colección 4.** Descripción del producto, periodo, resolución y leyenda:  
   https://peru.mapbiomas.org/iniciativas-y-productos/cobertura-y-uso-del-suelo/cobertura/

2. **MapBiomas Perú – Mapas de las Colecciones.** Descarga GeoTIFF y ruta del Asset de Google Earth Engine:  
   https://peru.mapbiomas.org/descargas/mapas-de-las-colecciones/

3. **MapBiomas Perú – Información de las Leyendas.** Códigos y descripción detallada por bioma:  
   https://peru.mapbiomas.org/descargas/informacion-de-las-leyendas/

4. **MapBiomas Perú – ATBD General, Colección 4.0 (2026).** Metodología y descripción de clases:  
   https://peru.mapbiomas.org/wp-content/uploads/sites/6/2026/10/ATBD-General-MapBiomas-Peru-Coleccion-4.0-ES.pdf

Los datos de MapBiomas son públicos y se distribuyen bajo licencia CC BY 4.0. Cita a MapBiomas Perú y especifica la Colección 4, el periodo consultado y la fecha de acceso.
