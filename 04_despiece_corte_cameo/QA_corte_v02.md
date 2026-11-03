# QA del despiece para Cameo — v02

Generado: 2026-10-22 · `Planos_montaje/generar_corte_cameo.py` (importa `generar_planos_warren.py` sin modificarlo) · Fuente: `Especificacion_Puente_Warren.xlsx` (sin modificar)

Resultado: **8 de 8 verificaciones correctas**.

## Verificaciones

| # | Verificación | Resultado | Detalle |
|---|---|---|---|
| 1 | Conjunto de ids v02 = v01 | OK | v01: 269 ids (contornos emparejados en los DXF v01: 269 de 289; 20 sin par = dibujos de detalle/catálogo). v02: 269 hojas, 269 ids únicos; faltantes 0 [], sobrantes 0 [], duplicados 0 []. |
| 2 | Piezas no modificadas: misma área y perímetro que en los DXF v01 (tol. 0,01) | OK | 219 hojas comparadas; diferencia máxima de área 0,0000 mm² y de perímetro 0,0000 mm; fuera de tolerancia: 0 []. (Las hojas en espejo conservan área y perímetro.) |
| 3 | Las 48 cartelas U siguen presentes y su cambio de área está documentado | OK | 48 cartelas U. U1: 4 hojas, 848,12 → 795,42 mm² (-52,70 c/u); U2: 8 hojas, 1163,24 → 1071,24 mm² (-92,00 c/u); U3: 8 hojas, 1163,24 → 1071,24 mm² (-92,00 c/u); U4: 8 hojas, 1152,50 → 1060,50 mm² (-92,00 c/u); U5: 8 hojas, 1163,24 → 1071,24 mm² (-92,00 c/u); U6: 8 hojas, 1163,24 → 1071,24 mm² (-92,00 c/u); U7: 4 hojas, 848,12 → 795,42 mm² (-52,70 c/u). Total H-05: -4101,6 mm². |
| 4 | Todo dentro de la zona útil, sin solapes y con separación ≥ 2 mm | OK | 13 tapetes; piezas fuera de la zona: 0; pares a menos de 2 mm: 0; separación mínima medida 2,454 mm; distancia mínima a la escuadra 2,500 mm. |
| 5 | Cada pieza tiene un rótulo dentro de ella (≥ 0,8 mm del borde) | OK | 273 hojas (con T00); sin rótulo: 0; con trazos a menos de 0,8 mm del borde: 0. Rótulos por debajo del alto pedido: 16 (A3 2,75 mm, A4 2,75 mm). |
| 6 | Cada pliegue, eje y ranura está dentro de su pieza | OK | 2095 líneas revisadas; fuera de su pieza: 0 []. |
| 7 | Relectura de cada DXF: polilíneas rojas cerradas = piezas; solo POLYLINE/LINE y colores permitidos; extensión = hoja | OK | 13 archivos; con error: 0 []. T00_PRUEBA.dxf: AC1009, rojas cerradas 4/4, tipos LINE/POLYLINE, colores 1/3/4/5/6/8, extensión x 0 a 235, y 0 a 300 / T01_v02.dxf: AC1009, rojas cerradas 18/18, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T02_v02.dxf: AC1009, rojas cerradas 18/18, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T03_v02.dxf: AC1009, rojas cerradas 16/16, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T04_v02.dxf: AC1009, rojas cerradas 14/14, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T05_v02.dxf: AC1009, rojas cerradas 22/22, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T06_v02.dxf: AC1009, rojas cerradas 20/20, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T07_v02.dxf: AC1009, rojas cerradas 24/24, tipos LINE/POLYLINE, colores 1/3/4/5/8, extensión x 0 a 235, y 0 a 300 / T08_v02.dxf: AC1009, rojas cerradas 32/32, tipos LINE/POLYLINE, colores 1/4/5/8, extensión x 0 a 235, y 0 a 300 / T09_v02.dxf: AC1009, rojas cerradas 28/28, tipos LINE/POLYLINE, colores 1/4/5/8, extensión x 0 a 235, y 0 a 300 / T10_v02.dxf: AC1009, rojas cerradas 34/34, tipos LINE/POLYLINE, colores 1/3/4/5/6/8, extensión x 0 a 235, y 0 a 300 / T11_v02.dxf: AC1009, rojas cerradas 27/27, tipos LINE/POLYLINE, colores 1/3/5/6/8, extensión x 0 a 235, y 0 a 300 / T12_RETENIDO_H01_v02.dxf: AC1009, rojas cerradas 16/16, tipos LINE/POLYLINE, colores 1/3/5/6/8, extensión x 0 a 235, y 0 a 300 |
| 8 | Área total frente a Lista_de_corte y al plano v01 | OK | v02 = 514 444,9 mm² (cortar 463 315,3 + retenida 51 129,6); plano v01 (DXF) = 518 666,5; Lista_de_corte = 500 895,7. v02 − v01 = -4 221,6 = H-05 -4 101,6 + PS1/PS7 sin pestaña -120,0 + otros -0,00. v01 − Excel = +17 770,7 (barras dobles +37 184, ingletes y VP/PS más cortas; ver QA_v01). |

## Tapetes

| Tapete | Archivo | Tipo | Hojas | Uso de la zona útil | Contenido |
|---|---|---|---|---|---|
| T00 | T00_PRUEBA.dxf | prueba | 4 | 9.2 % | PRUEBA ×4 |
| T01 | T01_v02.dxf | corte | 18 | 71.8 % | CS3 ×6, CS2 ×4, DW8 ×4, A1 ×4 |
| T02 | T02_v02.dxf | corte | 18 | 71.8 % | CS4 ×6, CS5 ×4, DW5 ×4, A6 ×4 |
| T03 | T03_v02.dxf | corte | 16 | 70.8 % | CS1 ×2, CS6 ×2, PE2 ×4, CI c3-t1 ×4, A0 ×4 |
| T04 | T04_v02.dxf | corte | 14 | 65.3 % | PE1 ×4, DW7 ×2, CI c1-t1 ×4, A7 ×4 |
| T05 | T05_v02.dxf | corte | 22 | 71.3 % | DW2 ×4, DW4 ×2, U1 ×4, TS ×12 |
| T06 | T06_v02.dxf | corte | 20 | 61.2 % | DW11 ×4, DW10 ×8, A2 ×8 |
| T07 | T07_v02.dxf | corte | 24 | 63.3 % | DW9 ×2, DW6 ×2, DW12 ×8, A5 ×8, U7 ×4 |
| T08 | T08_v02.dxf | corte | 32 | 54.0 % | DW1 ×8, DW3 ×8, CI c3-t2 ×4, CI c2-t1 ×4, A3 ×8 |
| T09 | T09_v02.dxf | corte | 28 | 56.7 % | CI c1-t2 ×4, CI c2-t2 ×4, CI c1-t3 ×4, A4 ×8, U2 ×8 |
| T10 | T10_v02.dxf | corte | 34 | 65.2 % | U3 ×8, U5 ×8, U6 ×8, U4 ×8, VP1 ×1, VP6 ×1 |
| T11 | T11_v02.dxf | corte | 27 | 58.7 % | VP0 ×1, VP7 ×1, PS ×7, TP ×4, GT ×14 |
| T12 | T12_RETENIDO_H01_v02.dxf | retenido | 16 | 78.4 % | VP2 ×4, VP3 ×4, VP4 ×4, VP5 ×4 |

## Decisiones aplicadas (Adrián, 22-oct-2026)

- Hoja de tapete 235 × 300 mm (300 en el sentido de avance), una hoja por tapete, sin retazos; zona útil 225 × 290 (margen 5). Prioridad: facilidad de uso sobre ahorro de material.
- Acomodo B: cada miembro o nudo completo en un mismo tapete (ninguna unidad partida).
- Rótulos de un solo trazo (Hershey «futural», ASCII). Alto de mayúscula 3 mm; 2.5 mm en tiras de 6 mm; 2.4 mm en tiras de 4 mm (TS y TP), con 0.8 mm de borde.
- Armadura B en espejo: cartelas y tiras B6 con k > tot/2 (misma área y perímetro).
- PS1 y PS7 sin la pestaña lateral hacia el extremo (en v01 quedaba 68 % fuera de U1/U7; con H-05, 45 %).
- H-05: cartelas U1-U7 al ras de la cuerda (+7 → +5) como override en el script, sin tocar el Excel. El PS baja 2 mm (tapa en y = 149) sin cambiar su hoja; la GT se pega en la cara de la cuerda y en la tapa del PS; altura 154 mm (154,6 con GT y TS).
- Cian en cartelas: ejes, contorno de cada miembro dentro de la cartela y cruz del nudo.
- Tubos: se pliegan con la cara dibujada hacia afuera.
- VP2-VP5 en un tapete aparte, contornos en rojo y aviso «RETENIDO H-01 - NO CORTAR» en gris (estado «retenida»).
- T00 en una hoja de tapete completa (mismo montaje que los tapetes reales).
- CONTROL_TAPETES en A3 vertical con la lámina a 1:1 y la lista con casillas.
- Planos v02: WA-02/03/04 muestran los tapetes de la Cameo en lugar de las hojas de carpeta.

## Supuestos y criterios (registrados)

- Ancho de corte con tapete de la Cameo 5 Alpha: 29,5 cm (11,6 in), según Silhouette America. Por eso los 235 mm van a lo ancho.
- Tiras más largas que 290 mm (CI c1-t2, 295 mm): inclinadas el ángulo mínimo con 0,6 mm de holgura (≈ 12,4°), enteras. Las de 289, 282, 271 y 255 mm van derechas, a lo largo del avance.
- Ids por hoja = ids de v01 (`pid` del script). En cartelas, el objeto Pieza agrupa 2 hojas; el id de cada hoja sale de su rótulo de v01 («A2 · 2/8» → A2-2/8).
- Armadura: hojas 1 a tot/2 = A; tot/2 + 1 a tot = B (cartelas, tiras DW B6 y tiras CI; en CI solo para el sobre, no hay espejo).
- Rótulos sin «k/tot» en VP (VP2B, VP2CJ1), PS (PS4) y GT (GT11), como en los ejemplos del encargo. Textos de orientación «ARRIBA», «ABAJO» y «EXTREMO» en VP y PS; marcas de nudo en los extremos de tubos y tiras B6.
- En A3 y A4 el rótulo no cabe a 3 mm sin cruzar ejes o contornos cian; queda en 2,75 mm (16 hojas), aceptado por Adrián el 22-oct-2026. Ver verificación 5.
- La escuadra de 100 × 100 se dibuja con el color de los rótulos (azul) en la esquina inferior izquierda de la zona útil.
- T00 agrega una ranura magenta de 5 mm en el cuadrado para probar ese color.
- Espesor de hoja t = 0,30 mm (S-07), igual que v01.

## Pendientes

- H-01: vigas VP2-VP5 (tapete retenido).
- H-02: apoyos de extremo; no hay piezas en v02 (no se inventaron).
- H-06: desarrollo por capa de los tubos de 2-3 capas; depende de la prueba P-06 (los tubos no cambiaron).
- Comprar Sketch Pens (la caja de la Cameo 5 Alpha no trae lapiceros).
- Actualizar el Excel (Lista_de_corte, masa) con las áreas de los planos cuando se cierren H-01, H-02 y H-06.
