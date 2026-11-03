# Revisión técnica independiente del diseño del puente Warren (IC-0610) — v01

Fecha: martes 20 de octubre de 2026 · Revisor: Claude (instancia independiente del autor del diseño) · Alcance: auditar; no se modificó ningún archivo original.

Unidades: fuerzas en kgf, longitudes en mm. P = carga total del puente (cuatro cargas P/4); cada armadura recibe P/2 y la carga de colapso del puente es 2 × la de una armadura modelada con P = 1 kgf, como en el ejemplo del curso [2, diap. 10].

## (i) Veredicto

1. **No conviene imprimir y cortar todo todavía.** La geometría, las fuerzas y los planos v01 están correctos y son consistentes entre sí (27 de 27 fuerzas, 269 piezas, escala 1:1 y PDF = DXF verificados).
2. El problema está en la carga y el apoyo reales: con la tabla rígida del ensayo, VP2 y VP5 reciben P/2 cada una y pueden fallar entre 12 y 24 kgf, según el ancho de la tabla (H-01). Además, aunque el apoyo es sobre placas planas, lo único que toca la placa son los cantos de 0,3 mm de las cartelas A0/A7, 2 mm por debajo de la cuerda (H-02).
3. La predicción de 21,5 kgf es una media de miembros. Por el efecto de eslabón débil, la mediana simulada es de 12-15 kgf; hoy el riesgo de perder puntos de predicción es alto (H-03).
4. Las GT no apoyan sobre la cuerda superior porque las cartelas U sobresalen 2 mm (H-05). Esto debilita el arriostramiento que justifica el diseño.
5. Se puede cortar ya lo que no depende de esos cambios (ver la sección vii). Hallazgos: Crítica 0 · Alta 4 · Media 6 · Baja 6.

## Fase 0 — Inventario de fuentes

| Fuente | Estado |
|---|---|
| Datos/2026 I - Proyecto del Puente IC-0610.pdf (enunciado, 5 págs.) | Leído completo, incluida la Figura 2 (imagen) |
| Datos/Descripción del Proyecto.pdf (diapositivas del curso, 10 págs.) | Leído: texto e imágenes (convención 2 × Pmáx, ejemplo de 6,768 kg y 48 g) |
| Especificacion_Puente_Warren.xlsx | Leído con valores y fórmulas; recalculado con LibreOffice: 0 diferencias y 0 errores. Las 2 celdas sin valor (Miembros!T25:T26) son "" a propósito (DW6/DW7 con F = 0) |
| Claude Doc «Especificación final del puente Warren (IC-0610)» | Leído completo con el conector de documentos |
| Artefacto «Diagrama de montaje del puente Warren» | Leído (HTML de 5 láminas) |
| Planos_montaje/v01 (WA_Juego, WA-01…05 PDF y DXF, QA_v01) | Verificados con scripts propios (r04, r05); el script del autor solo se leyó para ver parámetros |
| Planos_montaje/Manual de montaje.pdf | Revisado: es una impresión del diagrama de montaje (4 págs.) |
| MEMORIA_PROYECTO_PUENTE.md | Leído (§4-5 en detalle) |
| Datos/Resultados históricos de probetas (2 Excel y 63 .lvm) | Re-leídos desde los archivos crudos (r01, r02) |
| Ressler (2001), libro | Consultado: probetas p. 2-14/2-15, vigas de piso y prueba de carga, cap. 1 |
| Proyecto: claude/CRONOGRAMA_PROYECTO_PUENTE.md y claude/PLANOS_MONTAJE_v01.md | Leídos |
| Faltantes | Ninguno. «Tema 6 - Ejemplo 5 cercha vertical.pdf» no se usó (tutorial de SAP2000) |

## (ii) Requisitos del enunciado frente al diseño

| ID | Requisito (cita literal del enunciado [1]) | Diseño | Estado | Margen | Evidencia |
|---|---|---|---|---|---|
| REQ-01 | «Los estudiantes podrán construir un puente utilizando cualquiera de los tipos de armadura que se describen en la página 1-4 de la Referencia» (§3.4) | Warren trapezoidal sin montantes (Ressler p. 1-4: «Warren») | Cumple | — | Excel Resumen; WA-01 |
| REQ-02 | «…modelo de puente tipo armadura elaborado con cartón de carpetas de manila para archivo y goma blanca» (§1) | Carpeta de manila + goma para madera/blanca en todas las uniones y laminados | Cumple | — | WA-02 leyenda; WA-05 secuencia |
| REQ-03 | «Se recomienda limitarse a los materiales listados» (§3.2: carpetas, tijera, martillo, alfileres, regla, cuchilla, bolígrafo, papel mantequilla, tabla, goma para madera, prensas) | WA-02 pide «marcar con punzón»; MEMORIA §4.3 cita «cemento de contacto» (Ressler) | Cumple con observación | — | WA-02 leyenda; MEMORIA línea 108 (ver H-14) |
| REQ-04 | «Longitud: 700 ± 50 mm» (§3.4) | 671,4 mm total con cartelas (658 entre ejes de apoyo) | Cumple | 21,4 mm al mínimo (8 mm si se mide entre apoyos) | Excel Nudos!B23; r07 dimensiones |
| REQ-05 | «Ancho: 100 ± 10 mm» (§3.4) | 100 mm entre caras exteriores de tubos; 101,2 mm con cartelas de 2 capas | Cumple | 8,8 mm al máximo | Excel Supuestos!B18; r07 |
| REQ-06 | «Altura: 150 ± 10 mm» (§3.4) | 156 mm con cartelas; 156,6 con GT y TS; 144 entre ejes de cuerdas | Cumple | 3,4 mm al máximo (156,6); 4 mm al mínimo si se mide entre ejes | Excel Nudos!B24; WA-01 vista 05 |
| REQ-07 | «Paneles de la cuerda inferior: 100 mm ± 10 mm de longitud» (§3.4) | p = 94 mm, fijado por la plantilla 1:1 (no por medición en obra) | Cumple con margen menor a 5 mm | 4 mm al mínimo | Excel Supuestos!B4 |
| REQ-08 | «Vigas de piso: secciones tipo tubo de 15 mm × 6 mm (vigas transversales a nivel de cuerda inferior…)» (§3.4) | 8 VP T15×6, cara inferior en y = −3 (al ras de la cuerda inferior) | Cumple | — | Excel Secciones; WA-04; WA-05 det. 04 |
| REQ-09 | «La condición de carga… se describe en la siguiente figura» (Figura 2: cuatro cargas P/4) | P/4 en VP2–VP5 (A2–A5). Ensayo real (dato de Adrián): tabla apoyada en las 4 vigas y cargada al centro | Cumple el esquema; el modelo de reparto no | — | Excel Nudos D7:D10; ver H-01 |
| REQ-10 | «Los y las estudiantes deben buscar predecir la carga P de colapso» (§3.4) | P = 21,5 kgf (media de ensayos, FS = 1) | Cumple (calidad en duda) | — | Excel Resumen!B5; ver H-03 |
| REQ-11 | «Se recomienda enfáticamente la confección de las uniones entre elementos tal como se describe en los ejemplos de la referencia» (§3.4) | Cartelas en las dos caras de cada nudo (96 hojas) | Cumple | — | Excel Cartelas; WA-03 |
| REQ-12 | «…la inclusión de elementos estabilizadores para cargas fuera del plano tales como diafragmas u otros refuerzos» (§3.4) | 7 puntales PS, 12 tiras TS en X, 2 pórticos TP, 14 placas GT | Cumple con observación | — | WA-01 vistas 04-05; ver H-05 |
| REQ-13 | «La capacidad de los elementos… podrá estimarse a partir de los datos recopilados en el laboratorio y de los datos obtenidos en semestres anteriores» (§3.4) | Medias ponderadas de 2018-19, 2022 I, 2022 II y 2023 I | Cumple con observación | — | Excel Supuestos B22:E29; ver H-04 |
| REQ-14 | «Los elementos en tensión y en compresión… consistirán respectivamente de secciones tipo barra y tipo cajón» (§3.3) | Tensión: barras B6; compresión: tubos T10×10/T6×10; DW6-DW7 (fuerza 0) en cajón | Cumple | — | Excel Miembros M5:M31 |
| REQ-15 | «Cálculo de las fuerzas internas… Mediante cálculos manuales y software sugeridos en clase» (§3.5, nota ***) | Solver Python; SAP2000 (A-08) y verificación manual (A-09) pendientes | No verificable | — | Cronograma A-08, A-09 |
| REQ-16 | «El trabajo se hará en grupos de 4 o 5 estudiantes» (§3.1) | Grupo de 6 (Cronograma D-11) | No cumple (administrativo) | 1 integrante | Cronograma D-11; ver H-15 |
| REQ-17 | «Calidad constructiva del puente (10pts)» (§3.5) | Depende de la fabricación | No verificable | — | — |
| REQ-18 | «(10 %) Si la diferencia entre la resistencia calculada y la experimental es menor a 20%» (§3.5) | Probabilidad estimada de quedar dentro de ±20 % con 21,5 kgf: 0–24 % | En riesgo | — | r06_montecarlo; ver H-03 |

Sensibilidad a la tolerancia de corte: p = 94 está a 4 mm del mínimo, pero lo fija la plantilla impresa a 1:1, no una medición en obra. Un error de corte de ±1 mm por pieza no se acumula en la posición de los nudos. La altura (156,6) tiene 3,4 mm de margen al máximo: no conviene agregar nada por encima de la GT.

## (iii) Hallazgos

| ID | Severidad | Confianza | Dónde | Resumen | Corrección sugerida |
|---|---|---|---|---|---|
| H-01 | Alta | Probable | Excel Vigas_y_arriostres!B4:E6 y Resumen!B7; documento §Elementos transversales; WA-04 | El límite de la viga de piso (23,69 kgf) supone P/4 puntual en el centro de cada una de las 4 vigas y luz de 90 mm. | Pedir a la profesora el ancho, el espesor y la longitud de la tabla (C-08). Rehacer el chequeo de vigas con P/2 en VP2 y VP5, carga repartida en el ancho real. Reforzar VP2 y VP5 (más capas en el centro o cubrejuntas más largas) hasta que su P_lím ≥ 1,2 × P de la armadura. Comprobar en P-06 una viga reforzada a flexión. |
| H-02 | Alta | Confirmado (geometría) / Probable (falla) | Excel Cartelas_vertices A0 y A7 (y = −5); WA-05 det. 03; WA-01 | El puente apoya en placas planas (dato de Adrián: unos 7 cm a cada lado). Los puntos más bajos son los cantos de las cartelas A0/A7 (y = −5); la cuerda inferior y VP0 quedan 2 mm más arriba (y = −3). | Agregar un apoyo propio en cada extremo: un taco o zapata laminada bajo la cuerda inferior entre x ≈ −6,7 y 60, al nivel y = −5, o una viga de extremo en L como la AA' de Ressler (28 × 13 mm). Marcar en el plano la posición del puente sobre la placa. Confirmar con la profesora las placas y la condición fijo/móvil (C-09). |
| H-03 | Alta | Probable | Excel Resumen!B5 (21,52 kgf); documento §Predicción; Cronograma A-20 | La predicción usa la media de los ensayos y FS = 1, y el diseño está «balanceado»: con barras dobles, 10 miembros por armadura (20 en el puente) fallan entre 21,5 y 23,9 kgf; con la regla del Excel (n tiras) son 17 por armadura (hoja P_miembros, filas «dentro de +10 %»). | En el Informe de Avance, presentar la predicción con corrección por eslabón débil (por ejemplo, la mediana del Montecarlo correlado, ≈ 15 kgf) y un rango, o calibrarla con ensayos propios (P-06). Mantener 21,5 kgf como «resistencia media de miembros» y no como predicción. |
| H-04 | Media | Confirmado | MEMORIA_PROYECTO_PUENTE.md §5.1-5.2; Excel Supuestos!B23:D23 y B28:E29 (medias ponderadas) | MEMORIA toma el máximo bruto de cada .lvm: cuenta t4-1 (2022 II) como 1,582 kgf y no descuenta la línea base en t6-1 (1,49 kgf), c10x10x6-2 (−1,50), C2-10-10-10-3 (−0,78), c6x10x20-2 (−0,88) ni C8-6-10-20-1 (−0,39). | Re-procesar los .lvm con tara (script r01) y excluir t4-1, t6-1 y c6x10x20-2 con su motivo. Actualizar las medias en Supuestos y en la MEMORIA, y citar el procedimiento en el informe. |
| H-05 | Alta | Confirmado (geometría) / Probable (efecto) | Excel Cartelas_vertices U1-U7 (y relativo = +7); WA-01 vista 04; WA-04 det. GT; WA-05 | En los nudos superiores, la cartela sobresale 2 mm por encima de la cara superior de la cuerda (y = 151 frente a 149). Por eso la GT queda en y = 151 y solo se apoya en los cantos de 0,3-0,6 mm de las cartelas y en la tapa del puntal. | Recortar las cartelas U1-U7 al ras de la cara superior de la cuerda (cambiar +7 por +5 en Cartelas_vertices). Pegar la GT sobre la cuerda y el puntal, y regenerar WA-01, WA-03 y WA-04. Revisar con el grupo si la altura de 154 sigue siendo la deseada (D-19). |
| H-06 | Media | Probable | WA-02 (tubos de 2 y 3 capas: CS2-CS5, PE, DW2, DW11); Excel Secciones (desarrollo único 46/38 mm) | Todas las capas de un tubo se cortan con el mismo desarrollo (46 mm) y las mismas marcas, se laminan planas y luego se pliegan. | Antes de cortar en serie, fabricar en P-06 un CS3 de 3 capas y un PE de 2 capas. Si se arrugan, usar desarrollos por capa (46 / 47,9 / 49,8 mm, de adentro hacia afuera) o tubos anidados. Medir su sección y ensayarlos si es posible. |
| H-07 | Media | Confirmado | Documento «Especificación final del puente Warren» (Claude Doc): §Cuerda inferior, §Elementos transversales, §Decisiones por confirmar | Dice que las tiras de la cuerda inferior van «apiladas y pegadas entre sí en el plano medio, entre las cartelas», que la VP sale de una «hoja base de 48 × 100 mm», que el PS mide «29 × 90… entre los planos medios», que la capacidad de las barras es C = n × C1 y que siguen «por confirmar» la tira máxima, la posición de la VP y las GT. | Actualizar el documento con D-14 a D-19 o marcarlo como «superado por Planos_montaje v01» en las secciones afectadas. |
| H-08 | Media | Confirmado | Cronograma §5, P-06 («solape de 24 mm»), y §9, R-09 | La prueba de fabricación P-06 propone ensayar un empalme de la cuerda inferior con solape de 24 mm (del plano base, tiras de 4 mm). | Reescribir P-06: empalme de tiras de 6 mm con traslape de 30 mm, CS3 de 3 capas a compresión, nudo con cartela a tracción, VP2 reforzada a flexión y apoyo A0 (H-02). |
| H-09 | Media | Confirmado | Planos v01 (WA-02, WA-04) frente a Excel Miembros!O5:O31, Lista_de_corte y Resumen | Las barras dobles suman 37 184 mm² (≈ 7,6 g) sin aumentar P: rige la compresión (21,5-21,8 kgf) y las barras en tensión pasan a P ≥ 43 kgf. | Decidirlo en grupo. Si se mantiene, documentar que la cuerda inferior queda con reserva ≥ 2×. |
| H-10 | Baja | Confirmado | Excel Cartelas!I4:I18 («Fuerza máx. de miembro»), D4:D18; documento §Cartelas (regla g) | La columna «Fuerza máx. de miembro (kgf)» contiene las capacidades de los miembros (Miembros!S), no fuerzas. Las capas por cara (D) están escritas a mano y la regla g = ⌈1,25·F/(2·0,49·8)⌉ no explica sus constantes. | Corregir el rótulo y enlazar D con una fórmula. Documentar el origen de 0,49 y de 8. |
| H-11 | Baja | Confirmado | Excel Vigas_y_arriostres!B6:E6 (luz = Supuestos!B6 = 90) | El límite de la viga usa la luz entre planos medios (90 mm) y una carga puntual. | Usar la luz libre y la carga real (H-01). |
| H-12 | Baja | Confirmado | Excel Miembros!R5:R31 (interpolación con la columna I = largo de eje) | La capacidad a compresión se interpola con el largo de eje (94 / 151,48 mm). | Documentarlo como supuesto en «Propiedades de diseño». |
| H-13 | Baja | Confirmado | Artefacto «Diagrama de montaje del puente Warren» y Planos_montaje/Manual de montaje.pdf (impresión del diagrama; título de metadatos «Datos de falla de probetas - Claude») | Dibuja VP de 100 mm centrada en el eje inferior, PS de 90, barras B6 × n en el plano medio y miembros sin inglete; dice que las GT no se dibujan y lista como pendientes temas ya decididos. | Mover el manual a una subcarpeta «referencia_superada» o marcarlo como «no usar para cortar»; actualizar el título de sus metadatos. |
| H-14 | Baja | Confirmado | WA-02 leyenda («marcar con punzón»); MEMORIA §4.3 («cola con cemento de contacto») | Se mencionan un punzón y cemento de contacto, que no están en la lista de materiales recomendados del enunciado (§3.2). | Cambiar «punzón» por «alfiler o bolígrafo sin tinta» en WA-02 y aclarar en la MEMORIA que se usa solo goma. |
| H-15 | Media | Por verificar | Cronograma D-11 (grupo de 6); enunciado §3.1 y §3.3 | El grupo tiene 6 integrantes. | Confirmar por escrito con la profesora (C-11) y anotarlo como decisión en el Cronograma. |
| H-16 | Baja | Confirmado | Cronograma §1 (panel de estado y «Próxima acción») y D-09 | Todas las fases figuran al 0 % y la próxima acción es «F0 y F1 hoy lunes 19 oct». D-09 dice que el dibujo se hace en AutoCAD, pero los planos v01 se generan con Python a DXF/PDF. | Actualizar en la próxima sesión de planeamiento. |

### H-01 — Alta · Probable

- **Dónde:** Excel Vigas_y_arriostres!B4:E6 y Resumen!B7; documento §Elementos transversales; WA-04
- **Qué dice:** El límite de la viga de piso (23,69 kgf) supone P/4 puntual en el centro de cada una de las 4 vigas y luz de 90 mm.
- **Qué debería decir y por qué:** Con el método real de carga (tabla apoyada en VP2-VP5 y cargada al centro), la tabla es mucho más rígida que el puente: al flexionarse la armadura, la tabla se queda apoyada en VP2 y VP5, que reciben cada una P/2.
- **Evidencia:** Solver propio con tabla rígida (r08): reacciones A2 = A5 = 0,575, A3 = A4 = −0,075 (despegue). Viga con 4 capas (M = 133,26 kgf·mm): carga puntual P/2 → P_lím = 8·M/L = 11,8 kgf (L = 90) o 13,5 kgf (L = 78,8). Repartida en un ancho de tabla b (con L = 78,8): P_lím = 4·M/(L/2 − b/4) = 18,1 (b = 40), 21,9 (b = 60), 24,3 kgf (b = 70).
- **Impacto:** La viga de piso VP2/VP5 puede pasar a regir entre 12 y 24 kgf, según el ancho de la tabla. Los miembros que rigen la armadura (CS2/5, PE, DW1-3, DW10-12) no cambian su fuerza: CS3/CS4 y CI4 bajan 26 %. Pegado de las pestañas de VP2/VP5: cortante P/4 = 5,4 kgf frente a 7,2 kgf (uso 0,75).
- **Corrección sugerida (no aplicada):** Pedir a la profesora el ancho, el espesor y la longitud de la tabla (C-08). Rehacer el chequeo de vigas con P/2 en VP2 y VP5, carga repartida en el ancho real. Reforzar VP2 y VP5 (más capas en el centro o cubrejuntas más largas) hasta que su P_lím ≥ 1,2 × P de la armadura. Comprobar en P-06 una viga reforzada a flexión.

### H-02 — Alta · Confirmado (geometría) / Probable (falla)

- **Dónde:** Excel Cartelas_vertices A0 y A7 (y = −5); WA-05 det. 03; WA-01
- **Qué dice:** El puente apoya en placas planas (dato de Adrián: unos 7 cm a cada lado). Los puntos más bajos son los cantos de las cartelas A0/A7 (y = −5); la cuerda inferior y VP0 quedan 2 mm más arriba (y = −3).
- **Qué debería decir y por qué:** La reacción entra por un canto de cartón de 0,3 mm, sin respaldo en esos 2 mm, y su centro queda 11,5 mm hacia adentro del eje de A0. Ninguna fuente lo verifica ni lo detalla.
- **Evidencia:** A P = 21,5: reacción por armadura 5,38 kgf sobre 2 × 0,3 × 23 = 13,8 mm² → 0,39 kgf/mm² (3,8 MPa), es decir 24 % de la resistencia a tensión por área de una tira (1,66 kgf/mm²). El aplastamiento de un canto suelto no está ensayado. Con una placa de 70 mm desde el extremo (borde ≈ x = 63), la cartela A1 (desde x = 71) queda a 7,7 mm de tocarla.
- **Impacto:** Riesgo de aplastamiento local o de rotación en el apoyo antes de la carga predicha. Si el puente se coloca 8 mm más adentro, la reacción se reparte entre A0 y A1 y cambian las fuerzas de PE y DW1-DW2.
- **Corrección sugerida (no aplicada):** Agregar un apoyo propio en cada extremo: un taco o zapata laminada bajo la cuerda inferior entre x ≈ −6,7 y 60, al nivel y = −5, o una viga de extremo en L como la AA' de Ressler (28 × 13 mm). Marcar en el plano la posición del puente sobre la placa. Confirmar con la profesora las placas y la condición fijo/móvil (C-09).

### H-03 — Alta · Probable

- **Dónde:** Excel Resumen!B5 (21,52 kgf); documento §Predicción; Cronograma A-20
- **Qué dice:** La predicción usa la media de los ensayos y FS = 1, y el diseño está «balanceado»: con barras dobles, 10 miembros por armadura (20 en el puente) fallan entre 21,5 y 23,9 kgf; con la regla del Excel (n tiras) son 17 por armadura (hoja P_miembros, filas «dentro de +10 %»).
- **Qué debería decir y por qué:** El puente falla en el miembro más débil de muchos con resistencia dispersa (CV ≈ 30-40 %), así que su colapso esperado queda claramente por debajo del valor calculado con medias. La rúbrica da 10 puntos solo si el error es < 20 %.
- **Evidencia:** Montecarlo con remuestreo de 502 ensayos válidos (r06, η = 0,85): miembros independientes → mediana 12,4 kgf (P10 8,0; P90 13,8); correlación por semestre → mediana 15,1 kgf (P10 10,2; P90 22,3). Probabilidad de quedar dentro de ±20 % con 21,5: 0 % y 24 %. En el ejemplo del curso: predicción 5,06 y falla real 6,77 kgf (diseño no balanceado).
- **Impacto:** Error de predicción probable de 30-45 % (pierde 5 de 10 puntos) aunque el puente esté bien hecho.
- **Corrección sugerida (no aplicada):** En el Informe de Avance, presentar la predicción con corrección por eslabón débil (por ejemplo, la mediana del Montecarlo correlado, ≈ 15 kgf) y un rango, o calibrarla con ensayos propios (P-06). Mantener 21,5 kgf como «resistencia media de miembros» y no como predicción.

### H-04 — Media · Confirmado

- **Dónde:** MEMORIA_PROYECTO_PUENTE.md §5.1-5.2; Excel Supuestos!B23:D23 y B28:E29 (medias ponderadas)
- **Qué dice:** MEMORIA toma el máximo bruto de cada .lvm: cuenta t4-1 (2022 II) como 1,582 kgf y no descuenta la línea base en t6-1 (1,49 kgf), c10x10x6-2 (−1,50), C2-10-10-10-3 (−0,78), c6x10x20-2 (−0,88) ni C8-6-10-20-1 (−0,39).
- **Qué debería decir y por qué:** t4-1 es una señal plana (1,5804 a 1,5821 kgf en todo el archivo): no hubo ensayo y debe excluirse. Los picos deben medirse respecto a la línea base. t6-1 y c6x10x20-2 son ambiguos y conviene excluirlos con su motivo (criterio D-04).
- **Evidencia:** r01 (picos con tara) y r02 (re-cálculo): C1 de 6 mm = 2,985 kgf (Excel 2,963); de 8 mm = 4,216 (Excel 4,396); 10×10 de 100 mm = 3,747 (Excel 3,710); 10×10 de 160 mm = 3,032 (Excel 2,998). Con las capacidades re-calculadas, P = 21,78 kgf (rigen CS2/CS5).
- **Impacto:** Bajo en P (< 2 %), pero la sección «Propiedades de diseño de miembros» (9 puntos) y la lista de exclusiones D-04 quedarían con datos incorrectos.
- **Corrección sugerida (no aplicada):** Re-procesar los .lvm con tara (script r01) y excluir t4-1, t6-1 y c6x10x20-2 con su motivo. Actualizar las medias en Supuestos y en la MEMORIA, y citar el procedimiento en el informe.

### H-05 — Alta · Confirmado (geometría) / Probable (efecto)

- **Dónde:** Excel Cartelas_vertices U1-U7 (y relativo = +7); WA-01 vista 04; WA-04 det. GT; WA-05
- **Qué dice:** En los nudos superiores, la cartela sobresale 2 mm por encima de la cara superior de la cuerda (y = 151 frente a 149). Por eso la GT queda en y = 151 y solo se apoya en los cantos de 0,3-0,6 mm de las cartelas y en la tapa del puntal.
- **Qué debería decir y por qué:** El arriostre de techo (TS → GT → armadura) es lo que justifica tomar la cuerda superior como arriostrada en cada nudo (L = 94 fuera del plano). La unión GT-cuerda debe pegarse en una cara, no en cantos.
- **Evidencia:** Área de pegado GT-armadura: unos 2 × 30 × 0,6 = 36 mm² de canto más ≈ 80 mm² de tapa de PS (6 × 13,2), frente a 30 × 10 = 300 mm² si la GT apoyara en la cara de la cuerda. Si las cartelas U se recortan al ras (y rel. = +5), la altura total pasa a 154 mm (154,6 con GT y TS), todavía dentro de 140-160.
- **Impacto:** Arriostramiento fuera del plano poco confiable: puede provocar pandeo lateral de la cuerda superior (no modelado) antes de 21,5 kgf.
- **Corrección sugerida (no aplicada):** Recortar las cartelas U1-U7 al ras de la cara superior de la cuerda (cambiar +7 por +5 en Cartelas_vertices). Pegar la GT sobre la cuerda y el puntal, y regenerar WA-01, WA-03 y WA-04. Revisar con el grupo si la altura de 154 sigue siendo la deseada (D-19).

### H-06 — Media · Probable

- **Dónde:** WA-02 (tubos de 2 y 3 capas: CS2-CS5, PE, DW2, DW11); Excel Secciones (desarrollo único 46/38 mm)
- **Qué dice:** Todas las capas de un tubo se cortan con el mismo desarrollo (46 mm) y las mismas marcas, se laminan planas y luego se pliegan.
- **Qué debería decir y por qué:** Al plegar un laminado de 0,6-0,9 mm, cada capa exterior necesita más desarrollo que la interior (≈ +4 × π/2 × t ≈ +1,9 mm por capa con t = 0,30). Con capas iguales, las interiores se arrugan en las esquinas, la solapa se acorta y la sección exterior pasa de 10 mm. El factor η = 0,85 supone un laminado sano.
- **Evidencia:** CS3/CS4: 3 capas = 0,9 mm de pared en un tubo de 10 mm. Ningún ensayo de los datos históricos tiene más de 1 capa.
- **Impacto:** Riesgo de piezas mal plegadas y de menor capacidad en los miembros que rigen (CS2/CS5).
- **Corrección sugerida (no aplicada):** Antes de cortar en serie, fabricar en P-06 un CS3 de 3 capas y un PE de 2 capas. Si se arrugan, usar desarrollos por capa (46 / 47,9 / 49,8 mm, de adentro hacia afuera) o tubos anidados. Medir su sección y ensayarlos si es posible.

### H-07 — Media · Confirmado

- **Dónde:** Documento «Especificación final del puente Warren» (Claude Doc): §Cuerda inferior, §Elementos transversales, §Decisiones por confirmar
- **Qué dice:** Dice que las tiras de la cuerda inferior van «apiladas y pegadas entre sí en el plano medio, entre las cartelas», que la VP sale de una «hoja base de 48 × 100 mm», que el PS mide «29 × 90… entre los planos medios», que la capacidad de las barras es C = n × C1 y que siguen «por confirmar» la tira máxima, la posición de la VP y las GT.
- **Qué debería decir y por qué:** Los planos v01 usan barras dobles (n tiras en cada cara interior de cartela), VP de 88,8/89,4 mm y PS de 88,8/89,4 mm con pestañas, extremos a inglete y GT ubicadas (D-16 a D-19).
- **Evidencia:** Comparación entre fuentes (hoja «Fuentes» de Verificacion_v01.xlsx).
- **Impacto:** Quien corte o redacte con el documento obtendrá piezas o textos distintos de los planos.
- **Corrección sugerida (no aplicada):** Actualizar el documento con D-14 a D-19 o marcarlo como «superado por Planos_montaje v01» en las secciones afectadas.

### H-08 — Media · Confirmado

- **Dónde:** Cronograma §5, P-06 («solape de 24 mm»), y §9, R-09
- **Qué dice:** La prueba de fabricación P-06 propone ensayar un empalme de la cuerda inferior con solape de 24 mm (del plano base, tiras de 4 mm).
- **Qué debería decir y por qué:** El diseño usa tiras de 6 mm con traslape de 30 mm, laminadas en pilas por cara. Además, el documento recomienda ensayar tubos de 2-3 capas, un nudo con cartela y una viga de piso reforzada, y esos ensayos no están en el Cronograma.
- **Evidencia:** Excel Supuestos!B10 = 30; Cuerda_inferior; documento §Ensayos recomendados.
- **Impacto:** P-06 validaría un detalle que no se va a construir y dejaría sin probar los supuestos que rigen (η, τ, κ).
- **Corrección sugerida (no aplicada):** Reescribir P-06: empalme de tiras de 6 mm con traslape de 30 mm, CS3 de 3 capas a compresión, nudo con cartela a tracción, VP2 reforzada a flexión y apoyo A0 (H-02).

### H-09 — Media · Confirmado

- **Dónde:** Planos v01 (WA-02, WA-04) frente a Excel Miembros!O5:O31, Lista_de_corte y Resumen
- **Qué dice:** Las barras dobles suman 37 184 mm² (≈ 7,6 g) sin aumentar P: rige la compresión (21,5-21,8 kgf) y las barras en tensión pasan a P ≥ 43 kgf.
- **Qué debería decir y por qué:** Es una decisión discutible (Observación): el grupo prioriza el bono de resistencia/peso (D-05). La alternativa es poner n tiras en total, repartidas entre las dos caras (⌈n/2⌉ y ⌊n/2⌋), o una sola tira por cara en los miembros de n = 1, con P de tensión ≈ 22 kgf (igual que el Excel).
- **Evidencia:** Masa 101,9 → 105,5 g; resistencia/peso 211 → 204 (con P = 21,5).
- **Impacto:** −3,5 % en la relación resistencia/peso, sin ganancia de resistencia.
- **Corrección sugerida (no aplicada):** Decidirlo en grupo. Si se mantiene, documentar que la cuerda inferior queda con reserva ≥ 2×.

### H-10 — Baja · Confirmado

- **Dónde:** Excel Cartelas!I4:I18 («Fuerza máx. de miembro»), D4:D18; documento §Cartelas (regla g)
- **Qué dice:** La columna «Fuerza máx. de miembro (kgf)» contiene las capacidades de los miembros (Miembros!S), no fuerzas. Las capas por cara (D) están escritas a mano y la regla g = ⌈1,25·F/(2·0,49·8)⌉ no explica sus constantes.
- **Qué debería decir y por qué:** Rotular «Capacidad máx. de miembro que llega al nudo (kgf)» y calcular g con una fórmula enlazada a S y a τ, para que se actualice si cambian las capas.
- **Evidencia:** Por ejemplo, U3: 10,25 kgf = Miembros!S14 (capacidad de CS3).
- **Impacto:** Confusión al redactar; las cartelas no se actualizan solas.
- **Corrección sugerida (no aplicada):** Corregir el rótulo y enlazar D con una fórmula. Documentar el origen de 0,49 y de 8.

### H-11 — Baja · Confirmado

- **Dónde:** Excel Vigas_y_arriostres!B6:E6 (luz = Supuestos!B6 = 90)
- **Qué dice:** El límite de la viga usa la luz entre planos medios (90 mm) y una carga puntual.
- **Qué debería decir y por qué:** La luz libre de los planos es 78,8 mm; con la misma hipótesis de carga, P_lím = 27,1 kgf (+14 %). Queda superado por H-01.
- **Evidencia:** r07 viga_piso.
- **Impacto:** Conservador; sin efecto si se corrige H-01.
- **Corrección sugerida (no aplicada):** Usar la luz libre y la carga real (H-01).

### H-12 — Baja · Confirmado

- **Dónde:** Excel Miembros!R5:R31 (interpolación con la columna I = largo de eje)
- **Qué dice:** La capacidad a compresión se interpola con el largo de eje (94 / 151,48 mm).
- **Qué debería decir y por qué:** La longitud libre entre cartelas es menor (≈ 48 / 105 mm) y los extremos están restringidos por las cartelas, así que el criterio es conservador. Conviene declararlo en el informe.
- **Evidencia:** Cartelas de 46 mm de ancho en x y 20 mm de traslape por miembro.
- **Impacto:** Ninguno en seguridad; explica parte de la diferencia con un ensayo real.
- **Corrección sugerida (no aplicada):** Documentarlo como supuesto en «Propiedades de diseño».

### H-13 — Baja · Confirmado

- **Dónde:** Artefacto «Diagrama de montaje del puente Warren» y Planos_montaje/Manual de montaje.pdf (impresión del diagrama; título de metadatos «Datos de falla de probetas - Claude»)
- **Qué dice:** Dibuja VP de 100 mm centrada en el eje inferior, PS de 90, barras B6 × n en el plano medio y miembros sin inglete; dice que las GT no se dibujan y lista como pendientes temas ya decididos.
- **Qué debería decir y por qué:** Adrián confirmó que el grupo no lo usará para construir (solo referencia). Aun así, está guardado dentro de Planos_montaje.
- **Evidencia:** Comparación entre fuentes.
- **Impacto:** Bajo (por confirmación del usuario).
- **Corrección sugerida (no aplicada):** Mover el manual a una subcarpeta «referencia_superada» o marcarlo como «no usar para cortar»; actualizar el título de sus metadatos.

### H-14 — Baja · Confirmado

- **Dónde:** WA-02 leyenda («marcar con punzón»); MEMORIA §4.3 («cola con cemento de contacto»)
- **Qué dice:** Se mencionan un punzón y cemento de contacto, que no están en la lista de materiales recomendados del enunciado (§3.2).
- **Qué debería decir y por qué:** Usar alfiler o bolígrafo sin tinta para marcar pliegues y goma para madera en todas las uniones. La lista del enunciado es una recomendación.
- **Evidencia:** Enunciado §3.2.
- **Impacto:** Ninguno estructural; evita observaciones de la profesora.
- **Corrección sugerida (no aplicada):** Cambiar «punzón» por «alfiler o bolígrafo sin tinta» en WA-02 y aclarar en la MEMORIA que se usa solo goma.

### H-15 — Media · Por verificar

- **Dónde:** Cronograma D-11 (grupo de 6); enunciado §3.1 y §3.3
- **Qué dice:** El grupo tiene 6 integrantes.
- **Qué debería decir y por qué:** El enunciado dice «El trabajo se hará en grupos de 4 o 5 estudiantes» y «La conformación de los grupos… de entre cuatro y cinco integrantes, se realizará en clase». Si la profesora lo autorizó en clase, no hay problema, pero no hay registro.
- **Evidencia:** Cita literal del enunciado.
- **Impacto:** Administrativo; no afecta el diseño.
- **Corrección sugerida (no aplicada):** Confirmar por escrito con la profesora (C-11) y anotarlo como decisión en el Cronograma.

### H-16 — Baja · Confirmado

- **Dónde:** Cronograma §1 (panel de estado y «Próxima acción») y D-09
- **Qué dice:** Todas las fases figuran al 0 % y la próxima acción es «F0 y F1 hoy lunes 19 oct». D-09 dice que el dibujo se hace en AutoCAD, pero los planos v01 se generan con Python a DXF/PDF.
- **Qué debería decir y por qué:** Actualizar el panel y aclarar D-09 (los DXF se abren en AutoCAD).
- **Evidencia:** Cronograma v0.3.
- **Impacto:** Ninguno técnico.
- **Corrección sugerida (no aplicada):** Actualizar en la próxima sesión de planeamiento.

### Lo que sí está sólido (verificado de forma independiente)

- Geometría: los 15 nudos siguen la regla p/H; los 27 largos de eje y los 20 de corte cuadran (tol. 0,01). Largo 671,4; alto 156; ancho 100; panel 94: los cuatro dentro de los límites.
- Estática: mi solver de rigidez da m + r = 30 = 2j (isostática), reacciones de 0,5 / 0,5 y las 27 fuerzas iguales al Excel (diferencia máxima 0,0004). DW6 y DW7 tienen fuerza cero.
- Convención de P: coincide con la del curso (P total, P/4 por nudo en el modelo de una armadura, colapso del puente = 2 × Pmáx de la armadura).
- Capacidades: con los datos re-leídos desde los archivos crudos, las medias cambian menos de 4 % y P pasa de 21,52 a 21,78 kgf (CS2/CS5).
- Pegado miembro-cartela a P = 21,5 con τ = 0,04 y el peor inglete (82 %): uso máximo 0,72 (DW1). Empalme de CI4: uso 0,20. Cartela U3: esfuerzo medio = 14 % de la resistencia a tensión de referencia.
- Planos v01: 269 piezas, una por hoja de la lista esperada (48 tubos + 40 tiras DW + 28 tiras CI + 96 cartelas + 20 VP/cubrejuntas + 7 PS + 12 TS + 4 TP + 14 GT); todas dentro de la zona útil de 325 × 215, sin solapes; la más larga mide 295 mm. Son 9 hojas de carpeta (5 carpetas). Página de 1189 × 841 mm, controles de 100,0 mm en las 5 láminas, los 3605 vértices de corte del DXF están en el PDF y el texto mínimo es de 2,5 mm.
- Excel: 315 fórmulas sin errores al recalcular; el control de áreas de Resumen da 0; las 15 áreas de cartela coinciden con sus vértices.

## (iv) Puntos ya conocidos por el autor

| Ítem | Punto | Confirmación | Impacto |
|---|---|---|---|
| (a) | Área Excel 500 896 mm² frente a 518 666 mm² del plano; masa 101,9 frente a 105,5 g | Confirmado: Lista_de_corte!I72 = 500 895,73; planos 518 666 (QA_v01). Diferencia +17 771 mm² (+3,5 %, +3,6 g) = barras dobles +37 184 − ingletes 12 989 − VP/PS más cortas 6 424 mm² (QA_v01 cuadre). | Media: la masa y la relación resistencia/peso del informe (211) bajan a 204. No cambia P. |
| (b) | Tira máxima de 300 mm en Supuestos y 320 mm en los planos | Confirmado: Supuestos!B12 = 300; la pieza más larga de los planos mide 295,0 mm (r04). | Ninguno: todas las tiras cumplen ambos límites. |
| (c) | Sensibilidad dice 21,53 kgf/CS5 y Resumen 21,52/CS2 | Confirmado: valor fijo en Sensibilidad!B6 (21,53, rige CS5 en C6) frente a la fórmula Resumen!B5 (21,519). CS2 y CS5 son simétricos. | Ninguno (redondeo). |
| (d) | El empalme de la capa 2 cae en CI4 | Confirmado: Cuerda_inferior capa 2, traslape 305-335 en CI4. | Bajo ahora: con barras dobles cada tira lleva 1,46 kgf a P = 21,5 y el traslape resiste 7,2 kgf (uso 0,20). Con la tabla rígida (H-01), CI4 baja 26 %. |
| (e) | El Cronograma aún describe H = 140, panel de 100 y cargas a 200/300/400/500 (D-06, D-13, S-04, S-06) | Confirmado en Cronograma §3.1-3.2 y en el Anexo B. D-14 a D-19 ya registran la geometría nueva, pero D-06 no se corrigió. | Media para el informe (Descripción de la geometría): riesgo de citar cotas viejas. |
| (f) | η, κ, τ y t son supuestos sin ensayo | Confirmado. Sensibilidad del Excel: η = 0,60 → 18,6 kgf. κ no rige si se corrige H-01. τ: los usos de pegado calculados son ≤ 0,72 con τ = 0,04. t solo afecta luces libres (±0,1 mm) y la masa. | Alta en conjunto con H-03 y H-06: la predicción descansa en η sin ningún ensayo de tubos laminados. |

Ninguno de los hallazgos H-01 a H-16 estaba en la lista de puntos conocidos.

## (v) Lo que no se pudo verificar

- Resistencia al aplastamiento de un canto de cartón y resistencia del cartón a compresión en placa: no hay ensayos (H-02 y cartela U3).
- η (tubos laminados), κ (flexión de la viga de piso) y τ (goma): sin ensayos; solo hay estimaciones de sensibilidad.
- Pandeo fuera del plano de la cuerda superior y rigidez real del arriostre (TS, GT, pórticos): no se modeló en 3D; depende de H-05.
- Dimensiones de la tabla de carga y de las placas de apoyo: se usaron los datos aproximados de Adrián (tabla sobre las 4 vigas, placas de unos 70 mm).
- Modelo en SAP2000 (A-08) y verificación manual (A-09): todavía no existen.
- Espesor y gramaje de la carpeta real (t = 0,30 mm y 185 g/m² siguen sin medir).
- Calidad constructiva y resultado real del ensayo.

### Supuestos del revisor

- Pico de cada .lvm = máximo (o mínimo) menos la línea base, tomada como la mediana de las primeras muestras (hasta 300).
- Excluí t4-1 (señal plana), t6-1 y c6x10x20-2 (línea base corrida, pico ambiguo). La tensión de 2023 I queda excluida, igual que hizo el autor. Mantuve S-01 (c10x10x6 = 5 cm).
- La tabla de carga es rígida comparada con el puente, y las 4 vigas tienen la misma rigidez y el mismo nivel.
- Montecarlo: remuestreo de los ensayos válidos; barras como haz frágil (Daniels); tubos C1·(1 + η(n − 1)) con η = 0,85; correlación por semestre como escenario alternativo.
- Placas de apoyo de unos 70 mm medidos desde el extremo del puente (dato aproximado de Adrián).

## (vi) Consultas propuestas a la profesora (solo las envía Adrián)

| ID | Consulta |
|---|---|
| C-08 | Dimensiones (ancho, largo y espesor) y material de la tabla de carga que se apoya en las 4 vigas de piso. ¿Se apoya directamente sobre las vigas o con algún elemento que reparta la carga? ¿Se permite nivelar o calzar las vigas? |
| C-09 | Placas de apoyo: largo exacto (¿70 mm?), ancho, y si un extremo es fijo y el otro móvil. ¿Se permite un taco o zapata de cartón en los extremos de la cuerda inferior? |
| C-10 | ¿Cómo se miden la longitud (total o entre apoyos) y la altura (total con cartelas y techo o entre ejes)? Relacionado con S-06 y D-19. |
| C-11 | Confirmar que el grupo de 6 integrantes está autorizado (el enunciado indica grupos de 4 o 5). |

## (vii) Orden recomendado de correcciones antes de imprimir

1. H-01 (vigas de piso con el método de carga real): enviar C-08 y redimensionar VP2/VP5 antes de cortar las vigas.
2. H-02 (apoyos): diseñar el taco o zapata de extremo y marcar la posición sobre la placa; enviar C-09.
3. H-05 (GT sin apoyo en la cuerda): recortar las cartelas U al ras y regenerar WA-01, WA-03 y WA-04 como v02.
4. H-03 y H-04 (predicción y datos) para el Informe de Avance del viernes: re-procesar ensayos y presentar la predicción con su rango.
5. H-06 y H-08 (P-06): probar un CS3 de 3 capas, el empalme de 30 mm, el nudo, la VP reforzada y el apoyo antes del corte en serie.
6. Actualizar el Excel (conocido (a) y H-10/H-11), el documento (H-07) y el Cronograma (H-08, H-16, conocido (e)) y luego regenerar los planos v02.
7. Se puede cortar ya, sin esperar: tubos CS, PE y DW (tras la prueba de H-06), tiras CI y DW B6, PS, TS, TP y GT. No cortar todavía: VP2-VP5 (H-01), cartelas U1-U7 (H-05) ni piezas de apoyo (H-02).

## Archivos de esta revisión (Revision_diseno/v01)

- `INFORME_REVISION_v01.md`: este informe
- `Verificacion_v01.xlsx`: requisitos, hallazgos, fuerzas, capacidades, P por miembro, verificaciones, Montecarlo, comparación entre fuentes, QA de planos y ensayos (315 fórmulas, 0 errores)
- `scripts/r01_lvm_picos.py`: picos de los .lvm con línea base
- `scripts/r02_capacidades.py`: re-lectura y medias de los ensayos
- `scripts/r03_armadura.py`: solver de rigidez propio y P por miembro
- `scripts/r04_planos.py, r05_pdf_dxf.py`: verificación de piezas, escala y coincidencia PDF-DXF
- `scripts/r06_montecarlo.py`: eslabón más débil
- `scripts/r07_verificaciones.py`: verificaciones locales
- `scripts/r08_tabla_rigida.py`: reparto con tabla rígida
- `scripts/r09_excel.py, r10_informe.py, contenido_revision.py`: generación del Excel y del informe
- `salidas/`: resultados intermedios (CSV y JSON) y recálculo de LibreOffice

## Referencias

[1] A. Ramírez Villalba, «Proyecto de modelado de un puente — IC-0610 Mecánica de Sólidos II», Escuela de Ingeniería Civil, Universidad de Costa Rica, San José, Costa Rica, 2026.
[2] Escuela de Ingeniería Civil, UCR, «Proyecto: Modelado y construcción de un puente a partir de carpetas de manila», presentación del curso IC-0610, sep. 2025.
[3] S. J. Ressler, *Designing and Building File-Folder Bridges: A Problem-Based Introduction to Engineering*. West Point, NY, EE. UU.: United States Military Academy, 2001.
