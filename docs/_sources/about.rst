


MAX1704X Register Summary 
==========================

.. list-table:: Register Summary
   :widths: 15 20 15 35 10 10
   :header-rows: 1
   :align: center

   * - ADDRESS
     - REGISTER NAME
     - 16-BIT LSb
     - DESCRIPTION
     - READ/WRITE
     - DEFAULT
   * - 0x02
     - VCELL
     - 78.125µV/cell
     - ADC measurement of VCELL.
     - R
     - —
   * - 0x04
     - SOC
     - 1%/256
     - Battery state of charge.
     - R
     - —
   * - 0x06
     - MODE
     - —
     - Initiates quick-start, reports hibernate mode, and enables sleep mode.
     - W
     - 0x0000
   * - 0x08
     - VERSION
     - —
     - IC production version.
     - R
     - 0x001x
   * - 0x0A
     - HIBRT
     - —
     - Controls thresholds for entering and exiting hibernate mode.
     - R/W
     - 0x8030
   * - 0x0C
     - CONFIG
     - —
     - Compensation to optimize performance, sleep mode, alert indicators, and configuration.
     - R/W
     - 0x971C
   * - 0x14
     - VALRT
     - —
     - Configures the VCELL range outside of which alerts are generated.
     - R/W
     - 0x00FF
   * - 0x16
     - CRATE
     - 0.208%/hr
     - Approximate charge or discharge rate of the battery.
     - R
     - —
   * - 0x18
     - VRESET/ID
     - —
     - Configures VCELL threshold below which the IC resets itself, ID is a one-time factory-programmable identifier.
     - R/W
     - 0x96xx
   * - 0x1A
     - STATUS
     - —
     - Indicates overvoltage, undervoltage, SOC change, SOC low, and reset alerts.
     - R/W
     - 0x01xx
   * - 0x40 to 0x7F
     - TABLE
     - —
     - Configures battery parameters.
     - W
     - —
   * - 0xFE
     - CMD
     - —
     - Sends POR command.
     - R/W
     - 0xFFFF


Key Features
------------

- **Battery Compatibility:** Supports a single lithium cell.
- **Advanced SOC Tracking:** The ModelGauge™ algorithm continuously monitors the battery’s SOC under varying charge and discharge conditions.
- **Low Power Consumption:** Enters a 3µA hibernate mode automatically during low-current states, resuming activity when the system becomes active.
- **Temperature Compensation:** Managed through the system microcontroller for accurate performance across temperatures.
- **Debounced Initial SOC Estimate:** On battery insertion, the IC stabilizes the initial voltage readings for a more accurate SOC estimate.
- **I2C Interface:** Provides access to SOC, voltage, and rate information for easy integration with microcontrollers.
- **Compact Packaging:** Available in a 0.9mm x 1.7mm 8-bump wafer-level package (WLP) or a 2mm x 2mm 8-pin TDFN package.
