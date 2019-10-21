
# Unidad 1, asignación 1: datos espaciales en R

Por lo pronto, ayudaré con `...`. Donde quiera que los veas, deberás
sustituirlos por lo que indique el correspondiente mandato. “No te
aco’tumbre”.

## Mis primeros mapas en R con *simple features*

### Provincia asignada

Toma nota del código de tu provincia asignada aleatoriamente.

``` r
 # abreviatura provaleatoria
 #       acade            11
 #       agrie            09
 #       aleir            10
 #       arqco            16
 #       cindy            12
 #       franc            23
 #       geora            08
 #       hoyod            22
 #       ingan            07
 #       ingdi            19
 #       itac9            15
 #       ivanv            25
 #       lbine            30
 #       leona            24
 #       magda            20
 #       maryj            02
 #       masue            26
 #       mmvol            13
 #       naui2            29
 #       rober            27
 #       wilne            06
 #       yoenn            21
```

### Paquete `sf`

  - Carga el paquete `sf`, con el que podrás importar y manipular
    objetos *simple features*.

<!-- end list -->

``` r
library(...)
```

### Todas las provincias

  - Carga a la memoria la capa de provincias del archivo GeoPackage.
      - Primero determina cómo se denomina la capa de provincias usando
        la función `st_layers`. En esta función, escribe la ruta del
        archivo (el único GeoPackage dentro de la carpeta `data`. La
        ruta será algo tal que `data/...`). La función devolverá los
        nombres de las capas disponibles. Toma nota del nombre de la
        capa de provincias (es intuitivo).
      - Con dicha información, carga la capa de provincias con la
        función `st_read`, asignando al objeto `prov`. En el argumento
        `dsn` debes escribir la ruta del GeoPackage, y en `layer` el
        nombre de la capa.
  - Genera un mapa de todas las provincias usando todos los campos
    disponibles dentro de la capa (se deberían generar 4 mapas en un
    panel, uno por cada campo).
  - Genera un mapa de todas las provincias, pero sólo usando el campo
    `PROV`.

<!-- end list -->

``` r
st_layers(...)
prov <- st_read(dsn = '...', layer = '...')
plot(...)
plot(...['...'])
```

### Mi provincia asignada

  - Genera un mapa de tu provincia asignada usando el campo `PROV`. Nota
    que para elegir tu provincia asignada, necesitarás colocar el código
    de la misma dentro de los apóstrofos del índice de filas `prov$PROV
    %in% ''`.
  - Genera un objeto `sf` que sólo contenga tu provincia asignada
    mediante un subconjunto usando el índice de filas. Denomínalo
    `miprov`. La idea de crear este objeto es que puedas usarlo
    posteriormente.
  - Imprime el objeto `miprov` (sólo llámalo, no un `plot`).
  - Haz un `plot` de `miprov`, que mostrará un panel simbolizando tu
    provincia asignada de acuerdo con los campos disponibles.

<!-- end list -->

``` r
plot(...[prov$PROV %in% '', '...'])
... <- ...[prov$PROV %in% '', ]
...
plot(...)
```

## Cálculos, operaciones geométricas

Para hacer tus primeros mapas no realizaste cálculos ni ejecutaste
operaciones geométricas. A continuación, realizarás cálculos y
operaciones geométricas básicas. Necesitarás, además del paquete `sf` ya
cargado, necesitarás la colección `tidyverse`.

### Paquetes

``` r
library(tidyverse)
```

### Área provincial

  - Calcula el área de cada provincia y asígnala a una nueva columna
    denominada `areaenm2` dentro del propio objeto `prov`.
  - Muestra la tabla `prov` mostrando sólo las columnas `TOPONIMIA` y
    `areaenm2` recién creada. Se mostrará también la columna geométrica.

<!-- end list -->

``` r
prov$... <- st_area(...)
as.data.frame(prov[,c('...','...')])
```

### Ordenar provincias

  - Genera una tabla de provincias sólo con las columnas `TOPONIMIA` y
    `areaenm2`, y ordénalas de mayor a menor usando el campo `areaenm2`.
    Aunque puedes ejecutar una tubería de manera fluida y en una sola
    línea, te recomiendo hacerlo paso a paso, para que explores el
    efecto de cada verbo de la colección `tidyverse`.
      - Primero asegúrate de que el objeto `prov` está disponible,
        llamándolo. Verás que se trata de un objeto *simple feature*.
      - Deshazte de la columna geométrica, mediante la función
        `st_drop_geometry()`. Esto devolverá el objeto como `data.frame`
        (el objeto `prov` se mantendrá como `sf`, sólo estarás
        generando, en memoria, un `sf`).
      - Selecciona las columnas `TOPONIMIA` y `areaenm2`.
      - Organiza el resultado mediante la función `arrange`. Verás que
        se organizará ascendentemente.
      - Organiza descendentemente mediante la función `desc`.

<!-- end list -->

``` r
...
... %>% st_drop_geometry()
... %>% st_drop_geometry() %>% dplyr::select(..., ...)
... %>% st_drop_geometry() %>% dplyr::select(..., ...) %>% arrange(...)
... %>% st_drop_geometry() %>% dplyr::select(..., ...) %>% arrange(desc(...))
```
