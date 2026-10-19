# La deprivación urbana en Chile no es unidimensional

Trabajo del curso Métodos Multivariantes (Ingeniería Estadística, Universidad de Santiago
de Chile, 2026). Analizamos las 4.843 zonas censales urbanas del Censo 2017 junto con el
índice de deprivación territorial.

[Ver la presentación](https://cpizarrof.github.io/deprivacion-multivariante/)

## Resultados principales

El índice resume la deprivación de cada zona en un solo número. Con componentes
principales vimos que hacen falta tres dimensiones para describirla (75,6 % de la
varianza) y que el índice se relaciona casi solo con la primera: su correlación es 0,91
con la primera componente y −0,34 con la segunda.

Un grupo de 198 zonas con las peores condiciones de vivienda (29,3 % de población
extranjera, contra 4,5 % a nivel nacional) obtiene en el índice un valor más bajo que
zonas de la periferia tradicional. Para identificar ese grupo, el AUC baja de 0,993 a
0,650 cuando se usa solo el índice.

Además, buena parte de la variación ocurre dentro de las comunas (64,6 % en la primera
componente), así que comparar promedios comunales esconde diferencias importantes.

## Contenido

- `presentacion/`: fuente de la presentación (Quarto y reveal.js), estilos y datos.
- `codigo/`: el análisis completo en R y en Python, que se puede correr por separado.
- `docs/`: la presentación publicada en GitHub Pages.

## Cómo reproducirlo

Se necesita R (4.3 o más reciente) y [Quarto](https://quarto.org/docs/get-started/).

```r
install.packages(c("tidyverse", "knitr", "gt", "psych", "cluster",
                   "ellipse", "ggrepel", "showtext", "ragg"))
```

```bash
quarto render presentacion/presentaciondeprivacion.qmd
```

La primera vez tarda unos minutos, porque calcula las siluetas y los índices de Dunn
para todas las zonas; después queda en caché.

## Datos

`presentacion/datos_sin_geometry.csv` trae las 4.843 zonas con 11 indicadores del Censo
2017 y el índice de deprivación. Son datos agregados por zona, sin información de
personas. La cartografía no está en el repositorio por su tamaño.

## Métodos

Distancia de Mahalanobis, test de Mardia, T² de Hotelling, MANOVA, componentes
principales, análisis factorial con rotación varimax, clustering jerárquico y k-medias
(con silueta e índice de Dunn), análisis de correspondencia y regresión logística con
curva ROC.

## Autores

Nicole Gana, Carlos Pizarro y Camila Toloza. Profesor: Felipe Elorrieta López.
