# Cambio de Cobertura del Suelo en Cusco

Análisis multitemporal de la variación de cobertura entre áreas de bosque y zonas agrícolas mediante imágenes Landsat 8, LandTrendr y MapBiomas.

## Objetivo

Identificar y analizar la variación de cobertura del suelo en Cusco durante el periodo de estudio, con énfasis en la pérdida de áreas de bosque y su transición hacia zonas agrícolas.

Se busca determinar:

- Dónde ocurrieron los principales cambios de cobertura.
- Cuánta superficie de bosque se transformó en zona agrícola.
- Cómo evolucionaron estos cambios a lo largo del tiempo.
- Qué patrones espaciales y temporales presentan las áreas afectadas.

## Datos y herramientas

| Recurso | Aplicación |
|---|---|
| [Landsat 8 – USGS](https://www.usgs.gov/landsat-missions/landsat-8) | Imágenes satelitales para construir la serie temporal de cobertura. |
| [LandTrendr](https://developers.google.com/earth-engine/apidocs/ee-algorithms-temporalsegmentation-landtrendr) | Detección y caracterización de cambios en las trayectorias espectrales. |
| [MapBiomas Perú](https://peru.mapbiomas.org/) | Identificación y análisis de las clases de cobertura del suelo y sus transiciones. |
| [Google Earth Engine](https://earthengine.google.com/) | Procesamiento y análisis de imágenes satelitales. |

## Metodología

El proyecto se desarrollará en cuatro etapas:

### 1. Preparación de imágenes

- Delimitación del área de estudio.
- Obtención de imágenes Landsat 8.
- Filtrado de nubes y sombras.
- Generación de composiciones anuales.
- Cálculo de índices espectrales para el análisis de vegetación.

### 2. Detección temporal de cambios

Se utilizará LandTrendr para analizar las trayectorias espectrales de los píxeles e identificar posibles perturbaciones en la cobertura.

Se considerarán aspectos como el año, la magnitud y la duración de los cambios detectados.

### 3. Identificación de transiciones

Los cambios detectados se contrastarán con las clasificaciones anuales de MapBiomas Perú para identificar las transiciones entre bosque y zonas agrícolas.

Se prestará especial atención a:

- Bosque → Agricultura.
- Agricultura → Bosque.
- Permanencia de bosque.
- Permanencia de zonas agrícolas.

### 4. Cuantificación y análisis espacial

Se calcularán las superficies correspondientes a las transiciones identificadas, expresadas en hectáreas.

Se analizará su distribución espacial y evolución temporal para identificar las principales zonas de transformación.

## Resultados esperados

- Mapas anuales de cobertura de bosque y zonas agrícolas.
- Mapas de cambios y transiciones entre ambas coberturas.
- Cuantificación de superficies de pérdida y ganancia de bosque.
- Tablas de áreas por clase y transición.
- Identificación de zonas con mayor transformación de cobertura.
- Análisis de la evolución temporal de los cambios.

## Alcance

El análisis se concentrará en la variación de cobertura entre bosque y zonas agrícolas. La detección de cambios mediante LandTrendr y su interpretación temática mediante MapBiomas constituirán los componentes centrales de la metodología.

Los resultados serán incorporados al repositorio conforme avance el procesamiento y análisis de los datos.

## Referencias

- [Landsat 8 – USGS](https://www.usgs.gov/landsat-missions/landsat-8)
- [LandTrendr – Google Earth Engine](https://developers.google.com/earth-engine/apidocs/ee-algorithms-temporalsegmentation-landtrendr)
- [MapBiomas Perú](https://peru.mapbiomas.org/)
- [Google Earth Engine](https://earthengine.google.com/)