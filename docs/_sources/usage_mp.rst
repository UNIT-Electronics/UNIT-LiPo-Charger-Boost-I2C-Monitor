Micropython Usage
=================

.. note::

    This code has been tested on the RP2040 microcontroller of the `DualMCU <https://uelectronics.com/producto/unit-dualmcu-esp32-rp2040-tarjeta-de-desarrollo/>`_ board.


Method of Use
-------------
.. tip::

    The `max1704x.py` library is used to interact with the MAX1704X fuel gauge. To set up, download the library and save it onto the microcontroller. When using Thonny, ensure it is saved with the name `max1704x.py`.
        
        - `Library <https://github.com/UNIT-Electronics/MAX1704X_lib/blob/main/Software/MicroPython/example/max1704x.py>`_ 




Quick test: Copy this code and run it using Thonny:


.. code-block:: python

    from max1704x import max1704x

    mi_sensor = max1704x(sda_pin=12, scl_pin=13)

    print("I2C address of the sensor:", mi_sensor.address())

    mi_sensor.quickStart()

.. note::
    This version is adaptable to other boards, with a focus on close implementation.

The `Test.py` code outlines the primary usage and any special instructions. It's essential to execute this code on the RP2040 board.

- `Test <https://github.com/UNIT-Electronics/MAX1704X_lib/blob/main/Software/MicroPython/example/Test.py>`_

.. code-block:: python

    from max1704x import max1704x

    # Initialize max17043/max17048 with the pins

    # ESP32
    # _id=-1
    # SDA=21
    # SCK=22

    # RP2040
    _id=0
    SDA=12
    SCK=13
    my_sensor = max1704x(_id, sda_pin=SDA, scl_pin=SCK)

    # Get the I2C address of the sensor
    print("I2C address of the sensor:", my_sensor.address())

    # Get the version of the max1704x module
    print("Module version:", my_sensor.getVersion())

    # Get the remaining voltage in the cell
    print("Remaining cell voltage (V):", my_sensor.getVCell())

    # Get the state of charge
    print("State of charge (%):", my_sensor.getSoc())

    # Get the compensation value
    print("Compensation value:", my_sensor.getCompensateValue())

    # Get the alert threshold
    print("Alert threshold (%):", my_sensor.getAlertThreshold())

    # Check if the sensor is in alert
    print("Is in alert?:", "Yes" if my_sensor.inAlert() else "No")

    # Perform a quick start reset of the sensor
    my_sensor.quickStart()


MAX1704X Installation Guide Using MIP Library
----------------------------------------------

.. note::
    Direct support for mip on RP2040 is not available. The `mip` library is utilized to install the `max1704x.py` library.

Requirements
~~~~~~~~~~~~

- ESP32 device
- Thonny IDE
- Wi-Fi credentials (SSID and Password)

Installation Instructions
~~~~~~~~~~~~~~~~~~~~~~~~~

Follow the steps below to install the `max1704x.py` library:

Connect to Wi-Fi
~~~~~~~~~~~~~~~~

Copy and run the code below in Thonny to connect your ESP32 to a Wi-Fi network:

.. code-block:: python

    import mip
    import network
    import time

    def connect_wifi(ssid, password):
        wlan = network.WLAN(network.STA_IF)
        wlan.active(True)
        wlan.connect(ssid, password)

        for _ in range(10):
            if wlan.isconnected():
                print('Connected to the Wi-Fi network')
                return wlan.ifconfig()[0]
            time.sleep(1)

        print('Could not connect to the Wi-Fi network')
        return None


    ssid = "your_ssid"
    password = "your_password"
        
    ip_address = connect_wifi(ssid, password)
    mip.install('https://raw.githubusercontent.com/UNIT-Electronics/MAX1704X_lib/refs/heads/main/Software/MicroPython/example/max1704x.py')