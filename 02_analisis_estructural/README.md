# 02 · Análisis estructural

| Archivo | Descripción |
|---|---|
| `Especificacion_Puente_Warren.xlsx` | Fuente de verdad de la geometría, los miembros, los coeficientes de fuerza interna `k`, las capacidades y las masas |
| `Analisis_de_nodos_a_mano.pdf` | Desarrollo del método de nodos de una armadura con P = 1 kgf |
| `csibridge/Puente_Warren_CSiBridge.bdb` | Modelo de CSiBridge (base de datos `.bdb`) |
| `csibridge/Fuerzas_internas_CSiBridge.xlsx` | Fuerzas axiales obtenidas del modelo |

Convenciones: fuerzas en kgf, longitudes en mm, tensión positiva. Se modela una armadura con cuatro cargas de 0,25 kgf en los nudos centrales de la cuerda inferior; el puente tiene dos armaduras, por lo que la carga de colapso del puente es el doble de la de una armadura.

La comparación entre ambos métodos está en la sección 6 del informe de avance. En las cuerdas las diferencias son menores de 5 % (salvo CI1 y CI7, 7,1 %); en las diagonales llegan a 16,3 %. El informe señala que el modelo de CSiBridge todavía no reproduce del todo la idealización de armadura articulada, y por eso la predicción usa los valores del método de nodos.
