[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21148369&assignment_repo_type=AssignmentRepo)
# Proyecto integrador 1ra Entrega

## Integrantes
Camilo Correa
Ricardo Sabogal
Julian Rodriguez


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

![Plano de la galga - Grupo 8](images/PLANO%20GALGA%20GRUPO%208_page-0001.jpg)

[Ver plano completo del grupo 8 (PDF)](PLANO%20GALGA%20GRUPO%208.pdf)


## Periférico a trabajar

El periférico principal del proyecto es una **galga extensiométrica**, un sensor resistivo que permite medir **deformaciones mecánicas** en una superficie o estructura. Su principio de funcionamiento se basa en la **variación de la resistencia eléctrica** cuando el material al que está adherida se estira o comprime. 

### Principio de funcionamiento
Cuando la galga se somete a una tensión mecánica, su resistencia cambia proporcionalmente al esfuerzo aplicado. Este cambio suele ser muy pequeño (del orden de milésimas de ohmios), por lo que se requiere un **circuito amplificador de señal** antes de enviarla al microcontrolador. Para este propósito se utiliza generalmente un **amplificador de instrumentación** como el **HX711** o un amplificador operacional configurado como **puente de Wheatstone**.

La salida del amplificador se conecta a una entrada **ADC (conversor analógico-digital)** del **ESP32**, que digitaliza la señal para su posterior procesamiento y visualización.

### Conexión con el ESP32
- **Alimentación:** la galga y el amplificador operan con 5 V o 3.3 V según el módulo empleado.
- **Entradas analógicas:** el ESP32 recibe la señal amplificada en uno de sus pines ADC (por ejemplo GPIO34 o GPIO35).
- **Comunicación:** si se usa el módulo HX711, la lectura se realiza mediante protocolo digital con los pines `DT` y `SCK`.

### Aplicación en el proyecto
La galga permite **medir la fuerza o peso aplicado sobre una superficie**, y los datos adquiridos se procesan en el ESP32 para luego ser **transmitidos inalámbricamente** al nodo receptor mediante los **módulos RF de 433 MHz (ASK/FSK)**.  
De esta manera, el sistema puede monitorear en tiempo real el comportamiento del sensor sin necesidad de conexión física directa.

### Esquema funcional

[Galga extensiométrica] → [Amplificador / HX711] → [ESP32 (ADC o digital)] → [Módulo TX 433 MHz] → (Transmisión inalámbrica)


### Componentes involucrados
- Galga extensiométrica (sensor principal).  
- Módulo amplificador HX711.  
- Microcontrolador ESP32.  
- Fuente de alimentación de 5 V.  
- Módulo transmisor RF 433 MHz.  

El sistema permite medir, procesar y transmitir datos de fuerza o peso sin necesidad de una conexión física entre el sensor y el punto de monitoreo.

---

## 🧩 Avances

Durante el desarrollo del proyecto se realizó la **conexión e integración del sensor de galga con el módulo HX711 y el ESP32**, verificando la lectura correcta de datos desde el sensor y su comunicación estable con el microcontrolador.  

A continuación, se muestran las imágenes del montaje y pruebas iniciales:

<p align="center">
  <img src="images/galga%201.jpg" alt="Montaje galga - Imagen 1" width="500"><br>
  <em>Figura 1. Conexión del ESP32 con el módulo HX711 y la galga extensiométrica.</em>
</p>

<p align="center">
  <img src="images/galga%202.jpg" alt="Montaje galga - Imagen 2" width="500"><br>
  <em>Figura 2. Prueba práctica del sistema con carga aplicada.</em>
</p>

En las pruebas iniciales se comprobó la correcta alimentación del sistema, la detección de variaciones de señal en el HX711 al aplicar peso sobre la galga y la estabilidad de comunicación con el ESP32.  
Los próximos pasos incluirán la transmisión inalámbrica de los datos mediante el módulo **RF 433 MHz** y la validación de la lectura remota en el nodo receptor.

---


