Additional details
===================


The curves of power and output current of the MT3608 step-up converter for battery levels of 3.4V, 3.5V, and 3.7V show the variation of power and current as a function of the output voltage with a single-cell LiPo battery. The efficiency of the step-up depends on the input voltage: at high output voltages, close to 27V and with a battery voltage of approximately 3.4V, the maximum power is reduced to around 2-3W. However, for output voltages close to 5V, the output power stabilizes around 4W, even with a battery voltage of 3.4V. If the battery voltage is kept above 3.7V, the efficiency of the module increases, maintaining an average output power of 4W, as observed in the power and current curves.

.. caution:: 
     
        It is recommended to operate the module with a LiPo battery between 3.7V and 4.2V to maximize efficiency and output power. Alternatively, the module can also operate with a VIN input of 5V through the Type C USB port or the VIN input terminals, with a maximum limit of 6V.

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

This repository includes a folder with the `Fritzing models <https://github.com/UNIT-Electronics/UNIT-LiPo-Charger-Boost-I2C-Monitor>`_ of the module to facilitate its integration into diagrams and technical documentation of projects.


