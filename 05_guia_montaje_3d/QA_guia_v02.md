# QA de la guía de montaje 3D — v02 (con la pestaña Modelo)

Fecha: 2026-11-02T23:53:30. Fuentes: `piezas.json` y `pasos.json` (generados por `generar_guia.py`), `Corte_Cameo/v02/INVENTARIO_CORTE_v02` y los scripts de `Planos_montaje` (importados sin modificarlos).

**Resultado: todo correcto** (15 de 15 verificaciones correctas).

| Verificación | Resultado | Detalle |
|---|---|---|
| 1. Hojas en PEGAR | Correcto | 269 hojas; 269 aparecen en algún paso de PEGAR (269 como parte de una operación o de un resultado «listo sin pegar»; cada bolsa además se cuenta completa en «Abrir y revisar»). Faltan: 0; solo en revisar: 0. |
| 1b. Subensambles terminados en PEGAR | Correcto | 185 de 185 subensambles tienen al menos un paso de PEGAR que los deja listos. |
| 2. Subensambles en MONTAR | Correcto | 185 subensambles; 185 aparecen exactamente una vez en los 41 pasos de MONTAR. Repetidos: 0; sin paso: 0; desconocidos: 0. |
| 2b. Hojas por subensamble | Correcto | Las hojas de los 185 subensambles suman 269 y no se repiten. |
| 3. Conteos por bolsa = hoja «Tapetes» | Correcto | 1: 18; 2: 18; 3: 16; 4: 14; 5: 22; 6: 20; 7: 24; 8: 32; 9: 28; 10: 34; 11: 27; 12: 16 (total 269). |
| 3b. Cada subensamble sale de una sola bolsa | Correcto | Subensambles repartidos en dos bolsas: 0. |
| 3c. PEGAR usa solo piezas de su bolsa | Correcto | Pasos con piezas de otra bolsa: 0. |
| 4. Máximo 2 capas a la vez | Correcto | PEGAR: 127 operaciones; cada laminado une 2 hojas, cada capa o cubrejunta une 1 hoja a un laminado ya seco (con dependencia y 20 min de secado), cada plegado cierra 1 subensamble. Violaciones: 0; sin dependencia: 0. MONTAR: ninguna pieza nueva se apila sobre otra pieza nueva del mismo paso (0 casos); 16 traslapes de 30 mm de la cuerda inferior unen 2 tiras de la misma capa. |
| 5. Dimensiones del modelo 3D | Correcto | Largo 671.40 mm (v02: 671,4); alto 154.00 sin GT ni TS y 154.60 con ellas (v02: 154 / 154,6); ancho 100.00 entre caras exteriores de tubos (v02: 100) y 101.20 con cartelas. |
| 5b. Nudos y ejes | Correcto | 15 nudos = Excel (dif. máx. 0.0000 mm); cada nudo cae dentro de su cartela (15/15); el punto medio del eje de cada miembro cae dentro de su pieza 3D (40/40); armadura A en z > 0 y B en z < 0: sí. |
| 6. Volteo de Ressler: mitad exterior unida | Correcto | armadura A: 14 cartelas exteriores viajan en 1 bloque unido por tiras CI y B6; se pegan después del volteo: Cartela U4 · A · exterior; armadura B: 14 cartelas exteriores viajan en 1 bloque unido por tiras CI y B6; se pegan después del volteo: Cartela U4 · B · exterior. |
| 7. Fichas: área, masa y pasos | Correcto | 185 fichas. Área = suma de los contornos de sus hojas; masa = área × 185 g/m² × (1 + 0.1), igual que Resumen!B9 del Excel. Total 514447 mm² ≈ 104.7 g (Excel: 101.9 g con 500896 mm²; la diferencia son las barras dobles, los ingletes, las VP y PS a la luz libre y el recorte H-05 de las cartelas U). Paso de MONTAR y pasos de PEGAR de cada ficha = los de pasos.json. Errores: 0. |
| 8. Fichas: fuerza interna | Correcto | 344 filas de fuerza: k = hoja Miembros (col. K) y N = k · P/2 con P = 21.519 kgf (Miembros!I34, rige CS2); en barras B6, «por tira» = N / 2n (barras dobles). Tubos con la capacidad de la col. S; tramos CI con los miembros que cubre su capa; cartelas con los miembros que llegan al nudo (hoja Cartelas, traslapes). Errores: 0. |
| 9. Fichas: caja orientada de la vista con cotas | Correcto | 185 cajas con ejes ortonormales y sin reflejo (det = +1), medidas de mayor a menor. Coinciden con el diseño: tubos = largo de corte × sección (10 × 10 o 10 × 6), tiras B6 = largo × 6 × n·0,3, tiras CI = largo del tramo × 6 × 0,3, cartelas con g·0,3 de espesor, GT 30 × 24,44 × 0,3, TS y TP = largo × 4 × 0,3, VP y PS = luz libre de largo. Errores: 0. |
| Resumen | Correcto | PEGAR: 56 pasos en 12 bolsas (1: 6, 2: 6, 3: 5, 4: 4, 5: 4, 6: 5, 7: 5, 8: 4, 9: 3, 10: 6, 11: 3, 12: 5). MONTAR: 41 pasos. Subensambles: 185. Hojas: 269. |

## Prueba con Playwright (Chromium, WebGL por software)

| Prueba | Resultado | Detalle |
|---|---|---|
| Carga y 3D | Correcto | Página cargada en 731 ms; primera escena 3D (PEGAR) en 694 ms (construcción 41 ms); primera escena de MONTAR en 5 ms; puente completo (185 subensambles) en 39 ms. WebGL por software (SwiftShader): en una tableta o computadora con GPU debería ser más rápido. |
| Recorrido PEGAR | Correcto | 56 pasos hacia adelante con la flecha → y de regreso con ←; escena correcta en cada paso (56/56); vuelve al paso inicial; 6/6 capturas con 3D dibujado. |
| Recorrido MONTAR | Correcto | 41 pasos adelante y atrás; escena correcta en 41/41; 13/13 capturas con 3D dibujado (incluye el volteo de la mitad exterior a mitad de animación). |
| Botones y salto | Correcto | Siguiente ×2 y Anterior ×1 → M02; «Saltar a» el paso 21 → M21. |
| Marcar, desmarcar y recargar | Correcto | Marcar «Paso hecho» lo guarda; tras recargar sigue en M21 y marcado; se puede desmarcar. El avance queda solo en este navegador. |
| Mientras seca | Correcto | Con «CS3 · laminar capas 1 y 2» secando, la guía sugiere: Mientras seca: adelantar «CS2 · laminar capas 1 y 2» (bolsa 1). El botón lleva a «CS2 · laminar capas 1 y 2». |
| Temporizadores | Correcto | Al tocar «▶ 10:00» aparece un temporizador (10:00); al vencer cambia a «Ya se puede unir» y suena; se puede quitar. |
| Selección de bolsas | Correcto | [1] → 6 pasos, 18 hojas; [1,2] → 12 pasos, 36 hojas; [5,9] → 7 pasos, 50 hojas; [10,12] → 11 pasos, 50 hojas; [3,7,11] → 13 pasos, 67 hojas; [4,6,8] → 13 pasos, 66 hojas; [1,2,3,4,5,6,7,8,9,10,11,12] → 56 pasos, 269 hojas. Sin bolsas: pide elegir. Solo aparecen pasos de las bolsas marcadas. |
| Tableta y teléfono | Correcto | Sin desplazamiento horizontal en tableta (820 px) ni teléfono (390 px); tema oscuro revisado. |
| Modelo: abrir | Correcto | La pestaña 5 se abre sin pasar por «Antes de empezar» (es solo ver; PEGAR y MONTAR siguen bloqueados hasta leerla). 185 piezas dibujadas en 527 ms. |
| Modelo: tocar una pieza | Correcto | Clic sobre el centro de 10 piezas de 7 familias: 10/10 seleccionan la pieza tocada. La ficha de CS3 · A muestra nombre, medidas, fuerza (k = −0,816; N = −8,78 kgf), área y masa, bolsa 1 con sus 3 rótulos y sus 4 pasos; la vista 3D con cotas está dibujada. Al abrir la ficha el modelo no salta (6 px). |
| Modelo: cerrar la ficha | Correcto | Se cierra con ✕ y con la tecla Esc; al cerrar vuelven los colores normales. |
| Modelo: buscador y lista | Correcto | «vp2» → VP2; «cartela a3» → 4 piezas; el rótulo «DW1 1/8» → DW1-A-int; «bolsa 12» → 4 piezas (las de esa bolsa); «dw1» → 4 piezas, solo DW1 (no DW10–DW12); «cs» → 12 tubos de cuerda superior; «zzz» → ninguna. Enter elige la primera y centra la cámara en ella. |
| Modelo: aislar | Correcto | «Aislar pieza» deja 1 pieza a la vista; al quitarlo vuelven las 185. |
| Modelo: filtros | Correcto | Sin cuerda inferior: 157 piezas en 3D y 157 en la lista (esperado 157); sin armadura B además: 101 (esperado 101); «Mostrar todo» vuelve a 185. |
| Modelo: vista explotada | Correcto | Caja del modelo 671.4 × 154.6 × 101.2 mm → explotada 760 × 266.6 × 289.2 mm → vuelve a 671.4 × 154.6 × 101.2. Explotada, la cartela interior A3 (tapada en el modelo armado) se puede tocar: A3-A-int. |
| Modelo: ir a PEGAR y MONTAR | Correcto | «Ver en MONTAR» de VP2 abre M34 con todas sus piezas visibles (aunque en el Modelo estaban aisladas o filtradas); al volver al Modelo la ficha sigue abierta; «Ver en PEGAR» abre P12-1 y agrega la bolsa 12 a sus bolsas. En M41 se ven las 185 piezas. |
| Modelo: teléfono y tableta | Correcto | Teléfono de 390 px: las 5 pestañas caben; un toque abre la ficha como hoja inferior (de y = 338 a 844 px de 844); elegir en la lista sube la página al visor (DW1-A-ext). Sin desplazamiento horizontal en teléfono ni en tableta (820 px). |
| Autoría | Correcto | La línea «© 2026 Adrián Castro Ramírez · Escuela de Ingeniería Civil, Universidad de Costa Rica · Todos los derechos reservados · Acerca de» se ve en las 5 pantallas (intro, bolsas, pegar, montar, modelo); en PEGAR y MONTAR queda debajo de la barra de pasos sin taparla. «Acerca de» lleva al recuadro de créditos en «Antes de empezar», completo a la vista (autor, escuela y universidad, versión v02 · noviembre 2026, ayuda de Claude y three.js, derechos reservados). La página declara el autor en sus metadatos. Teléfono de 390 px sin desplazamiento horizontal. |
| Consola | Correcto | Sin errores en la consola en todas las pruebas (se ignoran las fuentes de Google si no cargan). |

Capturas (en `capturas/`): `01_antes_de_empezar.png`, `02_mis_bolsas.png`, `10_pegar_laminar_CS3.png`, `11_pegar_plegar_CS3.png`, `15_pegar_revisar_bolsa5.png`, `12_pegar_cartela_U3.png`, `14_pegar_puntales.png`, `13_pegar_cubrejunta.png`, `20_montar_M01_plano.png`, `21_montar_M03_cartelas.png`, `22_montar_M09_tubos.png`, `23_montar_M10_mitad_exterior.png`, `24_montar_M15_volteo.png`, `25_montar_M16_cartela_U4.png`, `26_montar_M17_armadura_A.png`, `27_montar_M33_voltear_A.png`, `28_montar_M34_vigas.png`, `29_montar_M36_bajar_B.png`, `30_montar_M38_GT.png`, `31_montar_M40_porticos.png`, `32_montar_M41_final.png`, `16_temporizador.png`, `17_mientras_seca.png`, `40_tableta_pegar.png`, `41_telefono_oscuro_intro.png`, `42_telefono_oscuro_M15.png`, `50_modelo_completo.png`, `51_modelo_ficha_CS3.png`, `52_modelo_buscar_VP2.png`, `53_modelo_aislar_VP2.png`, `54_modelo_filtros.png`, `55_modelo_explotado.png`, `56_modelo_explotado_cartela_interior.png`, `57_telefono_modelo.png`, `58_telefono_modelo_ficha.png`, `59_telefono_ficha_fuerza.png`, `60_tableta_modelo_ficha_CI.png`, `61_autoria_pie_modelo.png`, `62_autoria_acerca_de.png`, `63_telefono_acerca_y_pie.png`.

## Supuestos y decisiones registradas

- Producto: UHU Contact Power Adhesive (art. 63431). Ficha técnica: esperar 10–40 min, prensar 2–5 s, resistencia final a las 24 h, 15–30 °C, HR < 65 %, limpieza con acetona. Los 20 min entre capas los fijó Adrián (25 oct 2026). Seguridad tomada de la hoja de seguridad de la versión alemana (UHU Kontakt Kraftkleber flüssig, art. 64697).
- Una sola mano fina (prueba ya hecha por el grupo). Sin papel mantequilla y sin alfileres; las cartelas se fijan al plano con un pedacito de cinta de pintor en un borde (decisión de Adrián, 25 oct 2026).
- Montaje por el método de Ressler: la mitad exterior de cada armadura se arma boca abajo en la elevación espejo y se voltea de izquierda a derecha. La cartela U4 exterior no tiene tiras en esa mitad (DW6 y DW7 son tubos) y se pega después del volteo, como el nudo K de Ressler.
- Unión acostada: armadura A con la cara exterior abajo, VP y PS de pie, armadura B encima (girada media vuelta, sin voltear).
- Hoja k ≤ tot/2 = armadura A (también en tubos, que no tienen espejo). Dentro de cada armadura, primero la cara interior.
- La cuerda inferior se arma en MONTAR, sobre el plano, porque sus tiras vienen de las bolsas 3, 4, 8 y 9; en PEGAR solo se revisan.
- Cubrejuntas de VP2–VP5 en el dorso de la base (quedan por dentro del tubo), como en el corte de WA-05.
- Orden del techo según WA-05 v02: GT, luego TS, luego TP. T12 (VP2–VP5) ya cortado: se usa tal como está en v02.
- Avance guardado solo en el navegador de cada persona (Adrián pidió quitar el avance compartido).
- Espesor de hoja supuesto t = 0,30 mm (PARAM del script).
- v02, pestaña Modelo (decisión de Adrián, 2 nov 2026): selección por pieza armada (185 subensambles); ficha con medidas, fuerza interna, área y masa, bolsa, rótulos y pasos, y vista 3D con cotas; herramientas: vista explotada, filtros, buscador y aislar. Es solo ver: se abre sin la pantalla de seguridad.
- Fuerza interna: N = k · P/2 con k de la hoja Miembros (por kgf sobre una armadura) y P = carga de colapso predicha del puente (Miembros!I34). En barras B6 se muestra además la fuerza por tira suponiendo reparto igual entre las 2n tiras (barras dobles, D-17); la capacidad del Excel (n tiras) se duplica. VP2–VP5: P/4 al centro y M = (P/4)·L/4 con L = 90 mm (hoja Vigas_y_arriostres). PS, GT, TS y TP no llevan fuerza en el modelo plano.
- Masa de cada pieza = área de sus hojas × 185 g/m² × 1,10 (Supuestos!B14 y B15, como Resumen!B9).
- Autoría (decisión de Adrián, 2 nov 2026): línea de pie en todas las pantallas y recuadro «Acerca de» en «Antes de empezar»: creada por Adrián Castro Ramírez, Escuela de Ingeniería Civil, Universidad de Costa Rica; versión v02 · noviembre 2026; hecha con ayuda de Claude (Anthropic); © 2026 Adrián Castro Ramírez, todos los derechos reservados.
