# La deprivación urbana en Chile no es unidimensional

Análisis multivariante de **4.843 zonas censales urbanas** de Chile (Censo 2017), con
datos del índice de deprivación territorial.

**[→ Ver la presentación](https://Carloh97.github.io/deprivacion-multivariante/)**

Trabajo del curso Métodos Multivariantes, Ingeniería Estadística, Universidad de
Santiago de Chile.

---

## El hallazgo

El índice de deprivación que se usa habitualmente resume la carencia territorial en
**un solo número por zona**. Este trabajo pone a prueba ese supuesto y encuentra que
no se sostiene:

- Hacen falta **tres dimensiones**, no una. Las tres primeras componentes principales
  explican el 75,6 % de la varianza, y la segunda vale por sí sola el 24,7 %.
- El índice oficial **no ve la segunda dimensión**: correlaciona 0,907 con la primera
  componente, pero −0,337 con la segunda.
- Hay **198 zonas** con las peores condiciones de vivienda del país —29,3 % de
  población extranjera frente al 4,5 % nacional, y 3,1 % de hacinamiento crítico— a
  las que el índice asigna 0,29, **por debajo** de la periferia clásica (0,50).
- Ese grupo no se recupera desde el índice: el AUC para detectarlo cae de **0,993 a
  0,650**, y en su mejor umbral posible el índice necesita marcar **2.414 falsos
  positivos** para encontrar tres de cada cuatro de esas zonas.
- Y todo esto ocurre **dentro** de las comunas: el 64,6 % de la variabilidad de la
  primera componente es intracomunal. Comparar comunas promedia realidades opuestas.

---

## Qué hay en este repositorio

| Carpeta | Contenido |
|---|---|
| `presentacion/` | El código fuente de la presentación (Quarto + reveal.js), su hoja de estilos y la base de datos |
| `codigo/` | El análisis completo en R y en Python, en el estilo de los códigos del curso |
| `material/` | Guion de exposición, hoja resumen, guía teórica y notas técnicas |
| `docs/` | La presentación renderizada, que es lo que publica GitHub Pages |

---

## Cómo reproducirlo

**Requisitos:** R (≥ 4.3) y [Quarto](https://quarto.org/docs/get-started/).

Paquetes de R:

```r
install.packages(c("tidyverse", "knitr", "gt", "psych", "cluster",
                   "ellipse", "ggrepel", "showtext", "ragg"))
```

Para renderizar la presentación:

```bash
quarto render presentacion/presentaciondeprivacion.qmd
```

El primer render tarda unos minutos porque calcula las siluetas y los índices de Dunn
sobre las 4.843 zonas; después queda en caché.

Los archivos de `codigo/` son independientes de la presentación: reproducen el
análisis completo paso a paso y se pueden correr por separado.

---

## Datos

`presentacion/datos_sin_geometry.csv` contiene 4.843 zonas censales urbanas con 11
indicadores sociodemográficos del Censo 2017 más el índice de deprivación. Son datos
agregados a nivel de zona, sin información de personas.

La **cartografía** de las zonas censales no está en el repositorio por su tamaño (ver
`.gitignore`).

---

## Métodos

Análisis exploratorio y medidas de variabilidad · distancia de Mahalanobis y detección
de atípicos · test de Mardia · T² de Hotelling · MANOVA con Λ de Wilks y traza de
Pillai · elipsoides de confianza y de tolerancia · descomposición de la varianza ·
componentes principales · análisis factorial con rotación Varimax · clustering
jerárquico con cinco métodos de enlace · criterio de Mojena · silueta e índice de Dunn
· k-medias y CLARA · análisis de correspondencia simple · regresión logística con curva
ROC, índice de Youden y AUC.

---

## Autores

Nicole Gana · Carlos Pizarro · Camila Toloza

Profesor: Felipe Elorrieta López · Universidad de Santiago de Chile · 2026
