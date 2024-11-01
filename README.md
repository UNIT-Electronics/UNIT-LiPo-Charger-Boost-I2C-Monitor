# UNIT LiPo Charger Boost & I2C Monitor

El **UNIT LiPo Charger Boost & I2C Monitor** es un módulo avanzado de carga y monitoreo para baterías LiPo de una celda (3.7V a 4.2V) que integra un cargador TP4056, un elevador de voltaje MT3608 con salida limitada a 27V, y un monitor de batería MAX17048 a través de I2C. Este módulo es ideal para aplicaciones donde se requiere carga eficiente y monitoreo de la batería en tiempo real.

- **Carga de Batería LiPo**: Con dos opciones de corriente de carga seleccionables mediante pads (200 mA o 1 A).
- **Step-up MT3608**: Eleva el voltaje de la batería o de una entrada USB Tipo C hasta 27V, con una potencia nominal de salida de 4W.
- **Monitoreo de Batería**: El MAX17048 permite conocer el nivel de carga y voltaje de la batería mediante I2C.
- **Compatibilidad Qwiic/Stemma**: Conector JST con opción de energizar módulos Qwiic mediante el bus de voltaje del sistema.

## Características del Módulo

- **Voltaje de entrada (VIN)**: USB Tipo C a 5V o mediante pads de alimentación (máximo 6V).
- **Voltaje de carga de batería**: 3.7V nominal (4.2V máximo).
- **Potencia de salida**: Hasta 4W en el step-up MT3608, con eficiencia variable según el voltaje de entrada.
- **Conectores**:
  - JST de 2.0 mm para la batería LiPo.
  - Header de 2 pines (2.54 mm) para extraer el voltaje de batería.
  - Header de 5 pines para el monitor I2C de batería (MAX17048): `SDA`, `SCL`, `GND`, `QST` (reset), y `ALT` (alert).
- **Selección de corriente de carga**: Pad en la parte posterior para elegir entre carga de 200 mA o 1 A.
- **Compatibilidad Qwiic/Stemma**: Pad tipo jumper en la parte inferior para conectar el voltaje del sistema al conector Qwiic. *Advertencia: se recomienda una regulación adicional a 3.3V para cumplir con el estándar Qwiic*.

---

## Pinout

A continuación se muestran los diagramas de pinout del módulo para la parte frontal y posterior. Haz clic en cualquiera de las imágenes para más detalles en [UNIT Electronics](https://www.uelectronics.com).

### Pinout Frontal
[![Pinout Frontal](Docs/Pinouts/PinoutTop_ES.jpg)](https://www.uelectronics.com)

### Pinout Posterior
[![Pinout Posterior](Docs/Pinouts/PinoutBottom_ES.jpg)](https://www.uelectronics.com)

---

## Tabla de Conexión de Pines

La siguiente tabla detalla los pines de conexión principales del módulo **UNIT LiPo Charger Boost & I2C Monitor** para el header de 5 pines:

| PIN  | Descripción                   | Función en el MAX17048   |
| ---- | ----------------------------- | ------------------------ |
| SDA  | Línea de datos I2C            | Conectar a SDA del MCU   |
| SCL  | Línea de reloj I2C            | Conectar a SCL del MCU   |
| GND  | Tierra                        | Conectar a GND del MCU   |
| QST  | Reset del MAX17048            | Pin de reset (opcional)  |
| ALT  | Alerta de nivel de batería    | Pin de alerta (opcional) |

---

## Especificaciones Adicionales

- **Curvas de Caracterización**: Incluye las curvas de potencia de salida del step-up MT3608 para un voltaje de batería de 3.4V y 3.5V, mostrando cómo varía la potencia en función del voltaje de salida. La eficiencia del step-up depende del voltaje de entrada; a voltajes elevados próximos a 27V, la potencia máxima tiende a reducirse alrededor de 2-3W, mientras que para voltajes cercanos a 5V, la potencia de salida se estabiliza en aproximadamente 4W.
- **Advertencia de Uso**: El módulo debe operarse preferiblemente con una batería LiPo de entre 3.7V a 4.2V y con una entrada VIN de USB Tipo C a 5V o mediante los pads VIN, con un máximo de 6V.

## Carpeta de Modelos Fritzing

Este repositorio incluye una carpeta con los modelos de [Fritzing](Docs/Fritzing/UE0001-UNITBatteryChargerI2C.fzpz) del módulo para facilitar su integración en diagramas y documentación técnica de proyectos.

---

## Documentación

- **Biblioteca MAX1704X**: Este repositorio contiene una biblioteca para el control del MAX17048 usando Arduino IDE y MicroPython. Con esta biblioteca, puedes obtener información sobre el voltaje de la batería, el porcentaje de carga y el estado de descarga.

  [Repositorio MAX1704X](https://github.com/UNIT-Electronics/MAX1704X_lib)

  ### Compatibilidad
  - **Arduino IDE**
  - **MicroPython**

---

## Cómo Empezar

A continuación se presenta un ejemplo de cómo comenzar a usar el monitor MAX17048 en el módulo **UNIT LiPo Charger Boost & I2C Monitor**.

### Ejemplo en MicroPython

1. **Conexiones**:
   - Conecta el pin `SDA` del módulo al pin `SDA` de tu microcontrolador.
   - Conecta el pin `SCL` del módulo al pin `SCL` de tu microcontrolador.
   - Conecta `GND` a `GND` del microcontrolador.

2. **Instalación de la Biblioteca**:
   - Descarga la biblioteca MAX1704X desde el repositorio y asegúrate de incluirla en tu entorno de trabajo.

## Notas de Uso
**Selección de Corriente de Carga**: Utiliza los pads de la parte posterior para configurar la corriente de carga:

    - 200 mA: Ideal para cargas lentas, prolongando la vida de la batería.
    - 1 A: Carga rápida, recomendada para situaciones de carga de alta velocidad.
**Compatibilidad Qwiic**: Para usar el conector Qwiic/Stemma, asegúrate de cerrar el jumper del pad en la parte inferior si deseas alimentar los módulos conectados mediante el mismo bus de voltaje del sistema.

Con el UNIT LiPo Charger Boost & I2C Monitor, puedes monitorear el estado de tu batería, alimentar módulos Qwiic o periféricos a través del bus del sistema y obtener una potencia de salida estable en aplicaciones donde se requiera voltaje elevado.