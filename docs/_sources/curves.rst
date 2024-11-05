Additional details
===================


The power supply output of the MT3608 step-up is illustrated for a battery voltage of 3.4V and 3.5V, illustrating the impact of output voltage on power. The efficiency of the step-up is contingent upon the input voltage. At high voltages near 27V, the maximal power tends to diminish by approximately 2-3W, whereas the output power stabilizes at approximately 4W for voltages near 5V.

.. caution:: 
     
    The module should preferably be operated with a LiPo battery between 3.7V to 4.2V and with a USB Type C input VIN at 5V or through the VIN pads, with a maximum of 6V.

.. figure:: /_static/PvsV.png
   :align: center
   :alt: Curve
   :width: 80%
  
   Curve of Power vs Voltage



.. figure:: /_static/IvsV.png
    :align: center
    :alt: Graph
    :width: 80%
      
    Graph of Current vs Voltage

Fritzing models
===============

This repository includes a folder with the `Fritzing models <https://github.com/UNIT-Electronics/UNIT-LiPo-Charger-Boost-I2C-Monitor/blob/main/Docs/Fritzing/UE0001-UNITBatteryChargerI2C.fzpz>`_ of the module to facilitate its integration into diagrams and technical documentation of projects.


