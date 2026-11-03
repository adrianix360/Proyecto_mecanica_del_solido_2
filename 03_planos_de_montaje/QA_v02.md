# Planos de montaje Warren — v02

Cambios respecto de v01: H-05 (cartelas U al ras), PS1/PS7 sin pestaña al extremo, despiece para Cameo (tapetes 235 × 300) y armadura B en espejo. Generado con `generar_corte_cameo.py`, que importa `generar_planos_warren.py` sin modificarlo.

Generado: 2026-10-22 · Fuente: `Especificacion_Puente_Warren.xlsx` (leído con openpyxl, data_only=True)

## Archivos

- WA_Juego_v02.pdf
- WA-01_v02.pdf
- WA-01_v02.dxf
- WA-02_v02.pdf
- WA-02_v02.dxf
- WA-03_v02.pdf
- WA-03_v02.dxf
- WA-04_v02.pdf
- WA-04_v02.dxf
- WA-05_v02.pdf
- WA-05_v02.dxf

## Control de calidad

Errores: **0** · Avisos: 2

- OK: Dato clave p: Excel 94.0000 vs encargo 94.0 (tol 0.01)
- OK: Dato clave H: Excel 144.0000 vs encargo 144.0 (tol 0.01)
- OK: Dato clave B: Excel 90.0000 vs encargo 90.0 (tol 0.01)
- OK: Dato clave ancho: Excel 100.0000 vs encargo 100.0 (tol 0.01)
- OK: Dato clave eje diagonal: Excel 151.4761 vs encargo 151.48 (tol 0.01)
- OK: Dato clave ángulo: Excel 71.9239 vs encargo 71.92 (tol 0.01)
- OK: Dato clave largo total: Excel 671.4000 vs encargo 671.4 (tol 0.01)
- OK: Dato clave alto total: Excel 154.0000 vs encargo 154.0 (tol 0.01)
- OK: Dato clave corte CS: Excel 88.0000 vs encargo 88.0 (tol 0.01)
- OK: Dato clave corte diagonal: Excel 145.4761 vs encargo 145.48 (tol 0.01)
- OK: Dato clave hojas cartela: Excel 96.0000 vs encargo 96 (tol 0)
- OK: Dato clave área cartelas: Excel 100047.6800 vs encargo 100048.0 (tol 1.0)
- OK: Dato clave área total: Excel 500895.7335 vs encargo 500896.0 (tol 1.0)
- OK: Dato clave masa: Excel 101.9323 vs encargo 101.9 (tol 0.05)
- OK: Dato clave P: Excel 21.5192 vs encargo 21.5 (tol 0.05)
- OK: Dato clave TS: Excel 130.1384 vs encargo 130.14 (tol 0.01)
- OK: Dato clave TP: Excel 176.1959 vs encargo 176.2 (tol 0.01)
- OK: Largos de eje (27) y de corte (20) recalculados desde las coordenadas de Nudos: cuadran con Miembros (tol 0,01 mm)
- OK: Coordenadas de los 15 nudos = regla A_i = (p·i, 0), U_i = (p/2 + p(i−1), H)
- OK: Cotas rotuladas revisadas contra la geometría medida: 118
- OK: Ninguna pieza supera 320 mm (máximo 295.00 mm)
- OK: Filas de Lista_de_corte que deben cuadrar exacto (cartelas, cubrejuntas, TS, TP, GT, CI ×2): 30/30 dentro de 1 mm²
- OK: Textos: sin choques texto-texto ni texto-línea; alto mínimo 2,5 mm (mayúscula)
- OK: Vigas de piso: cuerpo entre caras interiores de cartelas (sin tocar diagonales ni cuerdas); pestañas dentro de la cartela
- OK: Despiece para Cameo: 13 tapetes de 235 × 300 dibujados a 1:1 en WA-02, WA-03 y WA-04 (detalle y QA en Corte_Cameo/v02)
- AVISO: VP0 y VP7 se corrieron 2,50 mm hacia adentro: en x = 0 / 658 chocaban con las tiras del pórtico (cara exterior de PE)
- AVISO: Inglete: el área de traslape bajo la cartela baja como máximo al 82 % (DW4 en A2) frente al extremo recto

Tapetes Cameo (235 × 300): **13** (T00 prueba, 11 de corte y 1 retenido).
Área de cartón: Excel 500 896 mm² → plano 514 445 mm² (+2.7 %).

## Cuadre con Lista_de_corte

| Pieza | Hojas Excel | Área Excel | Hojas plano | Área plano | Δ | Motivo |
|---|---|---|---|---|---|---|
| CS1 | 2 | 8096.00 | 2 | 7842.17 | -253.83 | inglete |
| CS2 | 4 | 16192.00 | 4 | 15684.35 | -507.65 | inglete |
| CS3 | 6 | 24288.00 | 6 | 23526.52 | -761.48 | inglete |
| CS4 | 6 | 24288.00 | 6 | 23526.52 | -761.48 | inglete |
| CS5 | 4 | 16192.00 | 4 | 15684.35 | -507.65 | inglete |
| CS6 | 2 | 8096.00 | 2 | 7842.17 | -253.83 | inglete |
| PE1 | 4 | 26767.60 | 4 | 25715.08 | -1052.52 | inglete |
| PE2 | 4 | 26767.60 | 4 | 25852.83 | -914.76 | inglete |
| DW1 | 4 | 3491.43 | 8 | 6816.36 | +3324.93 | barras dobles ×2 + inglete |
| DW2 | 4 | 26767.60 | 4 | 24740.47 | -2027.13 | inglete |
| DW3 | 4 | 3491.43 | 8 | 6816.36 | +3324.93 | barras dobles ×2 + inglete |
| DW4 | 2 | 13383.80 | 2 | 12370.24 | -1013.56 | inglete |
| DW5 | 2 | 1745.71 | 4 | 3408.18 | +1662.47 | barras dobles ×2 + inglete |
| DW6 | 2 | 11056.18 | 2 | 10524.72 | -531.46 | inglete |
| DW7 | 2 | 11056.18 | 2 | 10524.72 | -531.46 | inglete |
| DW8 | 2 | 1745.71 | 4 | 3408.18 | +1662.47 | barras dobles ×2 + inglete |
| DW9 | 2 | 13383.80 | 2 | 12370.24 | -1013.56 | inglete |
| DW10 | 4 | 3491.43 | 8 | 6816.36 | +3324.93 | barras dobles ×2 + inglete |
| DW11 | 4 | 26767.60 | 4 | 24740.47 | -2027.13 | inglete |
| DW12 | 4 | 3491.43 | 8 | 6816.36 | +3324.93 | barras dobles ×2 + inglete |
| Capa 1 tira 1 | 2 | 1944.00 | 4 | 3888.00 | +1944.00 | barras dobles ×2 |
| Capa 1 tira 2 | 2 | 3540.00 | 4 | 7080.00 | +3540.00 | barras dobles ×2 |
| Capa 1 tira 3 | 2 | 3060.00 | 4 | 6120.00 | +3060.00 | barras dobles ×2 |
| Capa 2 tira 1 | 2 | 3252.00 | 4 | 6504.00 | +3252.00 | barras dobles ×2 |
| Capa 2 tira 2 | 2 | 3468.00 | 4 | 6936.00 | +3468.00 | barras dobles ×2 |
| Capa 3 tira 1 | 2 | 1080.00 | 4 | 2160.00 | +1080.00 | barras dobles ×2 |
| Capa 3 tira 2 | 2 | 3384.00 | 4 | 6768.00 | +3384.00 | barras dobles ×2 |
| Cartela A0 | 4 | 2491.70 | 4 | 2491.70 | +0.00 | igual |
| Cartela A1 | 4 | 4203.78 | 4 | 4203.78 | +0.00 | igual |
| Cartela A2 | 8 | 8407.56 | 8 | 8407.56 | +0.00 | igual |
| Cartela A3 | 8 | 8306.40 | 8 | 8306.40 | +0.00 | igual |
| Cartela A4 | 8 | 8306.40 | 8 | 8306.40 | +0.00 | igual |
| Cartela A5 | 8 | 8407.56 | 8 | 8407.56 | +0.00 | igual |
| Cartela A6 | 4 | 4203.78 | 4 | 4203.78 | +0.00 | igual |
| Cartela A7 | 4 | 2491.70 | 4 | 2491.70 | +0.00 | igual |
| Cartela U1 | 4 | 3392.48 | 4 | 3181.68 | -210.80 | H-05: al ras de la cuerda |
| Cartela U2 | 8 | 9305.96 | 8 | 8569.96 | -736.00 | H-05: al ras de la cuerda |
| Cartela U3 | 8 | 9305.96 | 8 | 8569.96 | -736.00 | H-05: al ras de la cuerda |
| Cartela U4 | 8 | 9220.00 | 8 | 8484.00 | -736.00 | H-05: al ras de la cuerda |
| Cartela U5 | 8 | 9305.96 | 8 | 8569.96 | -736.00 | H-05: al ras de la cuerda |
| Cartela U6 | 8 | 9305.96 | 8 | 8569.96 | -736.00 | H-05: al ras de la cuerda |
| Cartela U7 | 4 | 3392.48 | 4 | 3181.68 | -210.80 | H-05: al ras de la cuerda |
| VP0 base | 1 | 4800.00 | 1 | 4021.20 | -778.80 | luz libre + pestañas |
| VP1 base | 1 | 4800.00 | 1 | 4171.20 | -628.80 | luz libre + pestañas |
| VP2 base | 1 | 4800.00 | 1 | 4142.40 | -657.60 | luz libre + pestañas |
| VP2 cubrejunta 1 | 1 | 4080.00 | 1 | 4080.00 | +0.00 | igual |
| VP2 cubrejunta 2 | 1 | 2880.00 | 1 | 2880.00 | +0.00 | igual |
| VP2 cubrejunta 3 | 1 | 1680.00 | 1 | 1680.00 | +0.00 | igual |
| VP3 base | 1 | 4800.00 | 1 | 4142.40 | -657.60 | luz libre + pestañas |
| VP3 cubrejunta 1 | 1 | 4080.00 | 1 | 4080.00 | +0.00 | igual |
| VP3 cubrejunta 2 | 1 | 2880.00 | 1 | 2880.00 | +0.00 | igual |
| VP3 cubrejunta 3 | 1 | 1680.00 | 1 | 1680.00 | +0.00 | igual |
| VP4 base | 1 | 4800.00 | 1 | 4142.40 | -657.60 | luz libre + pestañas |
| VP4 cubrejunta 1 | 1 | 4080.00 | 1 | 4080.00 | +0.00 | igual |
| VP4 cubrejunta 2 | 1 | 2880.00 | 1 | 2880.00 | +0.00 | igual |
| VP4 cubrejunta 3 | 1 | 1680.00 | 1 | 1680.00 | +0.00 | igual |
| VP5 base | 1 | 4800.00 | 1 | 4142.40 | -657.60 | luz libre + pestañas |
| VP5 cubrejunta 1 | 1 | 4080.00 | 1 | 4080.00 | +0.00 | igual |
| VP5 cubrejunta 2 | 1 | 2880.00 | 1 | 2880.00 | +0.00 | igual |
| VP5 cubrejunta 3 | 1 | 1680.00 | 1 | 1680.00 | +0.00 | igual |
| VP6 base | 1 | 4800.00 | 1 | 4171.20 | -628.80 | luz libre + pestañas |
| VP7 base | 1 | 4800.00 | 1 | 4021.20 | -778.80 | luz libre + pestañas |
| Puntales PS1–PS7 | 7 | 18270.00 | 7 | 17171.20 | -1098.80 | luz libre; PS1/7 sin pestaña ext. |
| Tiras en X de techo | 12 | 6246.64 | 12 | 6246.64 | +0.00 | igual |
| Tiras en X de pórticos | 4 | 2819.13 | 4 | 2819.13 | -0.00 | igual |
| Placas GT | 14 | 10264.80 | 14 | 10264.80 | +0.00 | igual |

## Parámetros fuera del Excel

- t_hoja = 0.3
- gap_inglete = 0.5
- barras_dobles = True
- pestana = 5.0
- holgura_portico = 0.5
- hoja_carpeta = (345.0, 235.0)
- margen_carpeta = 10.0
- largo_max = 320.0
- sep_piezas = 2.0
- sep_tiras = 0.0
- h_min = 2.5
