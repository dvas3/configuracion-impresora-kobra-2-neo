# Proyecto de configuracion de impresora

Este repositorio organiza la configuracion de una impresora Anycubic Kobra 2 Neo con Klipper.

## Estructura

- `documentos/impresora/`: archivos de configuracion y macros de la impresora 3D.
- `.gitignore`: reglas para evitar subir archivos temporales, respaldos accidentales y configuraciones locales del editor.

## Descripcion de cada archivo

### Archivos de impresora

- `documentos/impresora/printer.cfg`: configuracion principal de Klipper para la impresora Anycubic Kobra 2 Neo. Define MCU, ejes, extrusor, cama caliente, sonda, malla de cama, ventiladores, sensores de temperatura y tiempos de espera.
- `documentos/impresora/mainsail.cfg`: configuracion base de Mainsail con las secciones minimas del cliente, como tarjeta SD virtual, pausa/reanudacion, estado de pantalla y respuesta por consola.
- `documentos/impresora/macros.cfg`: coleccion de macros personalizadas para operacion y mantenimiento. Incluye arranque de impresion con gestion de malla, purga frontal, pausa y cancelacion seguras, carga y descarga de filamento, y utilidades de calibracion de cama.

## Uso de la configuracion

Esta estructura esta pensada para mantener separados los componentes principales de Klipper:

- `printer.cfg` actua como archivo principal y carga el resto mediante `include`.
- `mainsail.cfg` contiene la base minima esperada por Mainsail.
- `macros.cfg` concentra las macros operativas para impresion, mantenimiento y calibracion.

## Resumen de macros

El archivo `documentos/impresora/macros.cfg` esta organizado alrededor de cuatro bloques funcionales:

- macros auxiliares de estado y seguridad como `_SAFE_EXTRUDE`, `_SAFE_RETRACT` y `_PARK_HEAD`
- arranque de impresion con `START_PRINT`, `START_PRINT_MESH`, `START_PRINT_NO_MESH` y `PRINT_START`
- parada y control de impresion con `END_PRINT`, `CANCEL_PRINT`, `PAUSE`, `RESUME` y `M600`
- mantenimiento y mallado con `MESH_QUICK`, `MESH_PRECISE`, `_RUN_BED_MESH` y `LOAD_BED_MESH`

Comportamiento actual del arranque:

- `START_PRINT` calienta cama y nozzle, hace homing, carga o calibra la malla segun parametros y ejecuta una purga frontal compacta antes de mover al punto inicial
- `START_PRINT_MESH` fuerza una calibracion nueva de cama al inicio de la impresion
- `START_PRINT_NO_MESH` inicia la impresion sin compensacion de malla
- `_BED_MESH_START` permite tres modos: cargar un perfil guardado, calibrar una malla temporal o desactivar la malla

Cambios operativos relevantes:

- la extrusion y retraccion pasan por macros seguras que evitan mover filamento si el hotend no puede extruir
- `PAUSE`, `RESUME`, `END_PRINT` y `CANCEL_PRINT` guardan y restauran estado para aparcar el cabezal dentro de limites validos
- la purga se hace con `PURGE_LINE`, orientada al borde frontal y acotada al area util de la cama

## Restaurar o aplicar esta configuracion

Pasos recomendados en una instalacion con Klipper y Mainsail:

1. Hacer una copia de seguridad de la configuracion actual del equipo.
2. Copiar `documentos/impresora/printer.cfg` al directorio de configuracion de Klipper.
3. Copiar `documentos/impresora/mainsail.cfg` y `documentos/impresora/macros.cfg` al mismo directorio.
4. Verificar que los `include` de `printer.cfg` apunten a esos archivos.
5. Revisar el valor de `serial` en la seccion `[mcu]`, porque puede cambiar entre equipos.
6. Confirmar offsets, limites fisicos, temperaturas maximas y macros antes de imprimir.
7. Reiniciar Klipper y validar desde Mainsail que la configuracion carga sin errores.

## Recomendaciones antes de usarla en otra maquina

- Revisar el identificador USB de la MCU.
- Verificar que el tamano de cama y los finales de carrera coincidan con la impresora real.
- Confirmar que los valores de `rotation_distance`, `pressure_advance` e `input_shaper` pertenecen a esa maquina.
- Probar primero funciones seguras como `STATUS`, `HOME` o precalentamiento antes de iniciar una impresion real.

## Notas

- En el estado actual del proyecto solo habia archivos vinculados a la impresora.
