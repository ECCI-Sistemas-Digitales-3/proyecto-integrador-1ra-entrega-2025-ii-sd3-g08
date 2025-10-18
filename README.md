[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21148369&assignment_repo_type=AssignmentRepo)
# Proyecto integrador 1ra Entrega

## Integrantes
Camilo Correa
Ricardo Sabogal
Julian Rodriguez


## Arquitectura propuesta

## Arquitectura propuesta

La arquitectura propuesta se basa en una **GALGA** controlada por un **ESP32** que actúa como unidad central de adquisición y procesamiento. El diseño contempla una fuente de alimentación de 5 V, conexiones claras de alimentación (VCC/GND) y el mapeo de entradas y salidas entre el ESP32 y los periféricos del sistema, tal como se muestra en el plano de conexiones del grupo. 

### Componentes principales
- **Controlador:** ESP32 (unidad de procesamiento y comunicaciones).
- **Alimentación:** Fuente DC 5 V con rails VCC (+5 V) y GND.
- **Periféricos:** Sensores (entradas analógicas/digitales), actuadores y/o displays conectados a pines GPIO del ESP32 según el plano.
- **Conectividad interna:** Señales digitales/analógicas y buses de comunicación (UART/I²C/SPI) según se requiera por cada periférico.

### Flujo básico de la arquitectura
[Sensor / Entrada] -> [ESP32 (lectura ADC / digital)] -> [Procesamiento / Filtrado] -> [Salida / Display / Actuador o Comunicación]


### Notas sobre el plano de conexiones
- El plano **PLANO GALGA GRUPO 8** contiene el diagrama completo de conexión (alimentación, pines del ESP32 y referencias físicas de la galga).

##  Arquitectura propuesta

![Plano de la galga - Grupo 8](images/plano_galga_grupo8.png)


## 📄 Plano de conexiones
[Ver plano completo del grupo 8 (PDF)](PLANO%20GALGA%20GRUPO%208.pdf)


## Periférico a trabajar


## Avances

<!-- Subir en una carpeta src los códigos que tienen hasta el momento y esta sección agregar lo que consideren necesario referente a sus avances. -->
