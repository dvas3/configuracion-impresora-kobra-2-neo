# Proyecto de configuracion de impresora

Este repositorio organiza la configuracion de una impresora Anycubic Kobra 2 Neo con Klipper.

## Estructura

- `documentos/impresora/`: archivos de configuracion y macros de la impresora 3D.
- `.gitignore`: reglas para evitar subir archivos temporales, respaldos accidentales y configuraciones locales del editor.

## Descripcion de cada archivo

### Archivos de impresora

- `documentos/impresora/printer.cfg`: configuracion principal de Klipper para la impresora Anycubic Kobra 2 Neo. Define MCU, ejes, extrusor, cama caliente, sonda, malla de cama, ventiladores, sensores de temperatura y tiempos de espera.
- `documentos/impresora/mainsail.cfg`: configuracion base de Mainsail con las secciones minimas del cliente, como tarjeta SD virtual, pausa/reanudacion, estado de pantalla y respuesta por consola.
- `documentos/impresora/macros.cfg`: coleccion de macros personalizadas para operacion y mantenimiento. Incluye inicio y fin de impresion, pausas, purgas, mallado adaptativo, carga y descarga de filamento, precalentados y utilidades de calibracion.

## Uso de la configuracion

Esta estructura esta pensada para mantener separados los componentes principales de Klipper:

- `printer.cfg` actua como archivo principal y carga el resto mediante `include`.
- `mainsail.cfg` contiene la base minima esperada por Mainsail.
- `macros.cfg` concentra las macros operativas para impresion, mantenimiento y calibracion.

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
