Example Integration
===================

This example demonstrates how to integrate the UNIT LiPo Charger Boost & I2C Monitor with an ESP32 and display the battery status on an OLED screen.

.. caution:: 
   
   Since the Qwiic standard operates at 3.3V, it is recommended to use a voltage regulator after the JST output of the module to reduce VSYS to 3.3V and protect the Qwiic devices connected.


Steps to integrate the UNIT LiPo Charger Boost & I2C Monitor with the ESP32 and OLED display using the JST connector and I2C communication:

1. **Connect the JST Connector**: Attach the JST connector to the DualMCU board using the JST SH 1.0mm 4-pin connector.

2. **Connect the ESP32**: Link the ESP32 to the DualMCU board via the I2C communication protocol.

   .. figure:: /_static/qwiic.png
      :align: center
      :alt: ESP32
      :width: 50%
   
      JST SH 1.0mm 4-pin connected to ESP32.

3. **Solder the Battery Pin Configuration**: Solder the appropriate pads for the battery charger. Set the charge current (0.2 mA) depending on the battery specifications and connect the Vsys pad to configure the system voltage.

   .. figure:: /_static/back.png
      :align: center
      :alt: Back panel
      :width: 40%
   
      Pad soldering.

4. **Connect the OLED Display**: Connect the OLED display to the ESP32 using the I2C communication protocol.

5. **Upload the Code to the ESP32**: Copy the following code to the ESP32 and execute it using Thonny:

   .. code-block:: python 

      import machine
      import time
      from ocks import SSD1306_I2C
      from max1704x import max1704x

      i2c = machine.SoftI2C(sda=machine.Pin(21), scl=machine.Pin(22))
      oled = SSD1306_I2C(128, 64, i2c)

      my_sensor = max1704x(sda_pin=21, scl_pin=22)

      def update_display():
          oled.fill(0)  
          oled.text('UNIT Max', 25, 0) 

          vcell = my_sensor.getVCell()
          soc = my_sensor.getSoc()
          compensate_value = my_sensor.getCompensateValue()
          alert_threshold = my_sensor.getAlertThreshold()
          in_alert = my_sensor.inAlert()

          oled.text("Voltage: {:.2f}V".format(vcell), 0, 16)
          oled.text("SOC: {:.1f}%".format(soc), 0, 26)
          oled.text("Comp: {:.1f}".format(compensate_value), 0, 36)
          oled.text("Alert: {}".format("Yes" if in_alert else "No"), 0, 46)

          oled.show()  
          
      while True:
          update_display()  
          time.sleep(2)


6. **Monitor the Battery Status**: The OLED display will show the battery status, including the voltage, state of charge, compensation value, and alert status.

7. **Charge the Battery**: Connect the battery to the charger and monitor the charging status using the OLED display.

.. figure:: /_static/example.jpg
   :align: center
   :alt: Example Integration
   :width: 80%

   Example Integration of UNIT LiPo Charger Boost & I2C Monitor with ESP32 and OLED Display.