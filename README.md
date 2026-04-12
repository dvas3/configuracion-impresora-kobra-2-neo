# Proyecto de configuracion de impresora y conectividad

Este repositorio organiza los archivos del proyecto en categorias para que sea mas facil localizarlos y mantenerlos.

## Estructura

- `documentos/impresora/`: archivos de configuracion y macros de la impresora 3D.
- `documentos/wifi/`: carpeta reservada para documentos y configuraciones relacionadas con la red Wi-Fi.

## Descripcion de cada archivo

### Archivos de impresora

- `documentos/impresora/printer.cfg`: configuracion principal de Klipper para la impresora Anycubic Kobra 2 Neo. Define MCU, ejes, extrusor, cama caliente, sonda, malla de cama, ventiladores, sensores de temperatura y tiempos de espera.
- `documentos/impresora/mainsail.cfg`: configuracion base de Mainsail con las secciones minimas del cliente, como tarjeta SD virtual, pausa/reanudacion, estado de pantalla y respuesta por consola.
- `documentos/impresora/macros.cfg`: coleccion de macros personalizadas para operacion y mantenimiento. Incluye inicio y fin de impresion, pausas, purgas, mallado adaptativo, carga y descarga de filamento, precalentados y utilidades de calibracion.

### Archivos de Wi-Fi

- `documentos/wifi/README.md`: nota de estado de la carpeta de Wi-Fi. Actualmente no se encontraron archivos de este proyecto relacionados con la red inalambrica.

## Notas

- En el estado actual del proyecto solo habia archivos vinculados a la impresora.
- Si mas adelante se agregan archivos de red, deben colocarse en `documentos/wifi/` y documentarse tambien en este README.
