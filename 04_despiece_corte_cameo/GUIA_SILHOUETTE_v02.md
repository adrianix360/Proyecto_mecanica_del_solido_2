# Guía para cortar el puente Warren en la Cameo 5 Alpha (v02)

Fecha: 2026-10-22 · Archivos en `Corte_Cameo/v02` · Software: Silhouette Studio Basic (abre DXF).

## 0. Antes de empezar

- **Materiales:** la caja trae la AutoBlade (Type B), el adaptador para Sketch Pens y el tapete de 12 × 12 pulg, pero **no trae lapiceros**. Hay que comprar Sketch Pens de Silhouette (basta uno de cualquier color). La AutoBlade y el adaptador del lapicero van en el **portaherramientas 1**.
- **Hoja de tapete:** recorte cada hoja de carpeta cerrada (345 × 235) a **235 × 300 mm**, con esquinas a escuadra. Los 45 mm que sobran no se usan.
- **Archivos:** `T00_PRUEBA.dxf` (prueba), T01_v02.dxf a T11_v02.dxf (11 tapetes para cortar) y T12_RETENIDO_H01_v02.dxf (**RETENIDO H-01: no cortar todavía**).
- **Control:** imprima `CONTROL_TAPETES_v02.pdf` en A3 al 100 % (sin ajustar) y tenga a mano sobres rotulados (portada del PDF).

## 1. Preferencias de Silhouette Studio (una sola vez)

1. Abra **Edición → Preferencias** (en Mac: Silhouette Studio → Preferencias).
2. En **General**, ponga las unidades en **milímetros**.
3. En **Importar**, en la opción de archivos **DXF**, elija **«As-is» (tal cual)**, para que no cambie la escala ni la posición.
4. Cierre y vuelva a abrir Studio si lo pide.

## 2. Preparar la página y abrir el archivo

1. Panel **Configurar página**: máquina **CAMEO 5 / 5 Alpha**, tapete **CAMEO 12 × 12**, orientación **vertical**.
2. **Archivo → Abrir** y elija el DXF del tapete (tipo de archivo: DXF).
3. Seleccione todo (Ctrl+A) y agrúpelo. En el panel **Transformar/Posición** ponga X = 0 y Y = 0: el rectángulo gris de 235 × 300 queda en la esquina superior izquierda de la cuadrícula del tapete.
4. **Comprobación de escala:** el grupo debe medir 235.0 × 300.0 mm. La escuadra azul (abajo a la izquierda) mide 100 mm por lado. Si no coincide, revise el paso 1.3 y vuelva a abrir el archivo; no escale a mano.
5. Verifique que todo el dibujo (salvo el gris) quede dentro del **borde rojo de corte** que muestra Studio. La zona útil va de 5 a 230 mm a lo ancho y de 5 a 295 mm a lo largo.

## 3. Colocar el cartón en el tapete

1. Tapete limpio y con buena adherencia (si ya no pega, límpielo según el instructivo del tapete o cámbielo).
2. Ponga la hoja de 235 × 300 en la **esquina superior izquierda** de la cuadrícula, con el lado de 235 a lo ancho y el de 300 hacia abajo (sentido de avance). Alinee los bordes con las líneas de la cuadrícula y presione bien toda la hoja.
3. Cargue el tapete en la máquina (botón de carga).

## 4. Asignar acciones por color (panel Enviar → modo «Línea»)

| Color | Qué es | Acción |
|---|---|---|
| Azul | Rótulos y escuadra de 100 mm | Bolígrafo (Sketch Pen), portaherramientas 1 |
| Verde | Líneas de pliegue | Bolígrafo |
| Cian | Ejes, contornos de miembros y centro del nudo (cartelas) | Bolígrafo |
| Magenta | Ranuras entre pestañas (VP y PS) | Cortar con AutoBlade (antes que el rojo) |
| Rojo | Contorno de cada pieza | Cortar con AutoBlade (al final) |
| Gris | Borde de la hoja, zona útil, origen y textos de referencia | **Sin acción** |

**Orden recomendado: tres envíos sin descargar el tapete** (es la forma más simple y segura):

1. **Envío 1, bolígrafo:** active solo azul, verde y cian con la herramienta *Sketch Pen*. Coloque el lapicero en el adaptador, en el portaherramientas 1, y envíe.
2. **Pausa:** al terminar, **no descargue el tapete**. Revise que la escuadra y los rótulos salieron completos. Mida la escuadra con una regla (100,0 mm por lado). Cambie el lapicero por la **AutoBlade** en el mismo portaherramientas.
3. **Envío 2, ranuras:** active solo magenta (herramienta AutoBlade) y envíe.
4. **Envío 3, contornos:** active solo rojo (AutoBlade) y envíe.
5. Descargue el tapete. Si quiere hacerlo en un solo envío, Studio pide el cambio de herramienta entre acciones, pero con tres envíos es más fácil controlar el orden.

## 5. Corte de prueba (T00) y parámetros de partida

1. Corte primero `T00_PRUEBA.dxf` en una hoja de tapete completa (mismo procedimiento): cuadrado de 50 mm con una ranura de 5 mm, tira de 6 × 100, tubo T10×10 corto con pliegues y una cartela A2.
2. Material de partida en Studio: **Cartulina gruesa (Cardstock, Heavy)**. La AutoBlade ajusta la profundidad sola. Use **velocidad baja (2-3)** y **2 pasadas**, y ajuste la **fuerza** en pasos de 2-3 hasta que las piezas se suelten sin rasgar y sin cortar el tapete.
3. Si las esquinas de los ingletes o de las pestañas no se sueltan, active **«Line Segment Overcut» (sobrecorte de segmentos)** en las opciones avanzadas de corte.
4. Anote la fuerza, la velocidad y las pasadas que funcionaron y úselas en todos los tapetes.

## 6. Ajuste de distancia (si la escuadra no da 100,0 mm)

1. Mida con regla los dos lados de la escuadra azul y el cuadrado de 50 mm de T00.
2. Si difieren más de 0,3 mm, use **Ajuste de distancia (Distance Adjustment)** en la calibración de la máquina en Studio: dibuje o corte la línea de prueba, mídala e ingrese la medida. Repita T00.

## 7. Despegar, clasificar y armar

- Despegue las piezas **sin doblar las tiras**: voltee el tapete y doble el **tapete** (no el cartón) para que la pieza se suelte; use una espátula delgada para las cartelas.
- Marque cada pieza en la lista del tapete (CONTROL_TAPETES) y guárdela en su **sobre** (miembro o nudo; las cartelas y las tiras B6 llevan además la armadura A o B).
- **Armadura A y B:** en cartelas y tiras B6, las hojas con k ≤ tot/2 son de la armadura A y las demás de la B. Las de la B salieron **en espejo**: armando cada armadura sobre su elevación (WA-01: A normal, B en espejo), el lado dibujado queda siempre hacia arriba, con los ejes cian a la vista para ubicar los miembros.
- **Tubos:** se pliegan con la **cara dibujada hacia afuera** (pliegues verdes visibles al doblar). Las marcas de los extremos (por ejemplo A2 y U3) indican a qué nudo va cada inglete.
- **PS1 y PS7:** no tienen pestañas en la pared rotulada «EXTREMO»: esa pared mira al extremo del puente.
- **VP2-VP5:** quedan en su tapete RETENIDO hasta resolver H-01.

## 8. Consejos

- Tapete limpio, cartón plano y bien presionado; corte un tapete a la vez y clasifique antes de cargar el siguiente.
- Si una tira larga se levanta durante el corte, baje la velocidad y presione más el cartón antes de cargar.
- No cambie la escala ni mueva piezas en Studio: el inventario y el QA dependen de las posiciones del archivo.

## Fuentes

[1] Silhouette America, «Silhouette Cameo 5 Alpha», contenido de la caja y especificaciones (ancho de corte con tapete de 29,5 cm). https://www.silhouetteamerica.com/silhouette-cameo-5-alpha
[2] Silhouette America, «Silhouette Tool Compatibility» (AutoBlade Type B y Sketch Pens: portaherramientas 1). https://www.silhouetteamerica.com/tool-compatibility
[3] Silhouette America, «Sketch Pens» (compatibles con CAMEO5α). https://www.silhouetteamerica.com/sketch-pen

Nota: los nombres de menús pueden variar levemente según la versión de Studio; las fuentes oficiales están en inglés.
