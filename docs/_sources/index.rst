
UNIT LiPo Charger Boost & I2C Monitor
=====================================


Introduction
------------

The UNIT LiPo Charger Boost & I2C Monitor is an advanced charging and monitoring module for single-cell LiPo batteries (3.7V to 4.2V) that integrates a TP4056 charger, an MT3608 voltage booster with an output limited to 27V, and a MAX17048 battery monitor via I2C. This module is ideal for applications where efficient charging and real-time battery monitoring are required.

- **LiPo Battery Charging:** With two selectable charging current options via pads (200 mA or 1 A).
- **MT3608 Step-up:** Boosts the battery voltage or a USB Type C input up to 27V. With a maximum output power rating of 4W depending on the input voltage.
- **Battery Monitoring:** The MAX17048 allows you to know the battery's charge level and voltage via I2C.
- **Qwiic/Stemma Compatibility:** JST connector with the option to power Qwiic modules through the system voltage bus (VSYS -> VBAT-6V max).


.. image:: ./_static/max.png
   :align: center
   :alt: MAX17048
   :width: 80%



Module Features
---------------
- **Input Voltage (VIN):** USB Type C at 5V or through power pads (maximum 6V).
- **Battery Charging Voltage:** 3.7V nominal (4.2V maximum).
- **Output Power:** Up to 4W in the MT3608 step-up, with variable efficiency depending on the input voltage.
- **Connectors:**
  - 2.0 mm JST for the LiPo battery.
  - 2-pin header (2.54 mm) to extract the battery voltage.
  - 2-pin header (2.54 mm) to extract the output voltage from the MT3608 step-up.
  - 5-pin header for the battery I2C monitor (MAX17048): SDA, SCL, GND, QST (reset), and ALT (alert).
- **Charging Current Selection:** Pad on the back to choose between 200 mA or 1 A charging.
- **Qwiic/Stemma Output Compatibility:** This module is ready to connect the I2C lines (SDA and SCL) and ground (GND) to the Qwiic/Stemma connector, ensuring compatibility in communication with devices that use this standard. It also includes a jumper pad on the bottom that, when closed, allows the system voltage (VSYS) to be sent to the Qwiic/Stemma connector to power the modules connected through this bus. VSYS can vary between the battery voltage (3.7V) up to a maximum of 6V (Vin).

.. caution:: 
   
   Since the Qwiic standard operates at 3.3V, it is recommended to use a voltage regulator after the JST output of the module to reduce VSYS to 3.3V and protect the Qwiic devices connected.

DataSheet and Technical Reference
----------------------------------

.. raw:: html

   <div style="text-align: center;">
      <button style="background-color: #87cefa; color: white; border: none; padding: 10px 30px;" onclick="window.open('./_static/max17048-max17049.pdf', '_blank')">    MAX1704x  </button>
   </div>
   <br> </br>
   <iframe src="./_static/max17048-max17049.pdf" style="width:100%; height:500px;" frameborder="1"></iframe>
   <br> </br>


.. toctree::
   :maxdepth: 2
   :caption: Contents
 
   about
   generalboardcontrol
   curves
   jst
   usage_c
   usage_mp
   example
   report
