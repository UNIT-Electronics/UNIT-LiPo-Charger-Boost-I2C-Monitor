C++ Usage 
==========

The supports for module with c++ are the same as the c language, but with the addition of the c++ features.

`MAX1704X_lib <https://github.com/UNIT-Electronics/MAX1704X_lib/blob/main/Software/Duino/README.md>`_

Installation
------------
To install the library, download the library from the link above and add it to the Arduino IDE. To add the library to the Arduino IDE, follow the steps below:

1. Open the Arduino IDE.
2. Install the available version of **Adafruit MAX1704X**.

.. figure:: /_static/library.png
    :align: center
    :alt: Adafruit MAX1704X
    :width: 80%

    Manager Libraries


.. figure:: /_static/install.png
    :align: center
    :alt: Adafruit MAX1704X
    :width: 30%

    Install Library Adafruit MAX1704X

.. note::
    It is advised to employ the `DualMCU <https://uelectronics.com/producto/unit-dualmcu-esp32-rp2040-tarjeta-de-desarrollo/>`_ to utilize connectors with the QWIIC method. The implementation code is designed for this board; however, it may be altered to accommodate other compatible boards.


3. Copy the example code below and paste it into the Arduino IDE.


.. code-block:: cpp

    #include "Adafruit_MAX1704X.h"

    Adafruit_MAX17048 maxlipo;

    void setup() {
    Serial.begin(115200);
    while (!Serial) delay(10);    // wait until serial monitor opens

    Serial.println(F("\nAdafruit MAX17048 simple demo"));

    if (!maxlipo.begin()) {
        Serial.println(F("Couldnt find Adafruit MAX17048?\nMake sure a battery is plugged in!"));
        while (1) delay(10);
    }
    Serial.print(F("Found MAX17048"));
    Serial.print(F(" with Chip ID: 0x")); 
    Serial.println(maxlipo.getChipID(), HEX);
    }

    void loop() {
    Serial.print(F("Batt Voltage: ")); Serial.print(maxlipo.cellVoltage(), 3); Serial.println(" V");
    Serial.print(F("Batt Percent: ")); Serial.print(maxlipo.cellPercent(), 1); Serial.println(" %");
    Serial.println();

    delay(2000);  // dont query too often!
    }


4. Compile and upload the code to the board.

.. figure:: /_static/serial_monitor.png
    :align: center
    :alt: Arduino IDE
    :width: 60%




Acknowledgment
--------------

It should be noted that Adafruit is the creator of the library, and that UNIT-Electronics did not create it in-house. We would like to express our appreciation to Adafruit for their efforts, as well as to the open-source community for their ongoing support in the use and growth of this library through their contributions.