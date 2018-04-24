:mod:`sensors` - Working with Sensors
=====================================

The :mod:`sensors` module provides a collection of classes to interact with sensors, such as temperature, light, and soil moisture sensor.

.. _temp_sensor:

Temperature/Humidity Sensor
------------------------------

.. image:: https://media.digikey.com/Photos/Seeed%20Technology%20Ltd/101020011_sml.JPG
    :width: 200px
    :height: 200px

.. class:: sensors.TemperatureSensor(port[=3])

    Allows reading temperature and humidity information from the Grove Temperature Sensor based on DHT11. We recommend that this sensor be connected to Port 3, which is the default for this class. The ``port`` parameter defines which port the sensor is connected to.

    .. method:: TemperatureSensor.get_temperature(celsius[=False])

        Returns the temperature reading in Fahrenheit. If ``celsius`` is set to ``True`` then the celsius temperature will be returned.

        .. note::

            This temperature sensor offers a resolution of 1 degree Celsius. If you want more accurate readings, please try the pro version below.

    .. method:: TemperatureSensor.get_humidity()

        Returns the relative humidity in percentage.

    .. method:: TemperatureSensor.show_data(screen, line)

        Shows the temperature (in Fahrenheit) and relative humidity on the specified ``screen`` object on the specified ``line``. Also returns a tuple of the same temperature in Fahrenheit and relative humidity to avoid repeated readings on the sensor.

Example
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    from sensors import TemperatureSensor() 
    t = TemperatureSensor() # defines a temperature sensor at default port (Port 3)

    t.get_temperature() # returns the Fahrenheit value
    t.get_temperature(True) # returns the Celsius value
    t.get_humidity() # returns the humidity value

.. _temp_sensor_pro:

Temperature/Humidity Sensor Pro
----------------------------------

.. image:: https://static.generation-robots.com/3637-large_default/grove-temperature-and-humidity-sensor-pro.jpg
    :width: 200px
    :height: 200px

.. class:: sensors.TemperatureSensorPro(port[=3])

    Allows reading temperature and humidity information from the Grove Temperature Sensor Pro based on DHT22 (AM2302). We recommend that this sensor be connected to Port 3, which is the default for this class. The ``port`` parameter defines which port the sensor is connected to.

    .. method:: TemperatureSensorPro.get_temperature(celsius[=False])

        Returns the temperature reading in Fahrenheit. If ``celsius`` is set to ``True`` then the celsius temperature will be returned.

        .. note::

            This temperature sensor offers a resolution of .1 degree Celsius.

    .. method:: TemperatureSensorPro.get_humidity()

        Returns the relative humidity in percentage.

    .. method:: TemperatureSensorPro.show_data(screen, line)

        Shows the temperature (in Fahrenheit) and relative humidity on the specified ``screen`` object on the specified ``line``. Also returns a tuple of the same temperature in Fahrenheit and relative humidity to avoid repeated readings on the sensor.

.. code-block:: python

    from sensors import TemperatureSensorPro 
    t = TemperatureSensor(3) # defines a temperature sensor pro at default port (Port 3)

    t.get_temperature() # returns the Fahrenheit value
    t.get_temperature(True) # returns the Celsius value
    t.get_humidity() # returns the humidity value

    # shows temperature/humidity data on the oled screen
    from displays import OledScreen

    screen = OledScreen(6)
    t.show_data(screen, 1)

.. _light_sensor:

Light Sensor
------------------------------

.. image:: https://raw.githubusercontent.com/SeeedDocument/Grove-Digital_Light_Sensor/master/img/Digital_Light_Sensor.jpg
    :width: 200px
    :height: 200px

.. class:: sensors.LightSensor(port[=6], address[=0x29])

    Allows reading lux values from the Grove Digital Light Sensor based on the TSL2561 I2C light sensor. The ``port`` parameter cannot be any other number than 6, and the sensor can be connected to the board through an I2C hub. The ``address`` parameter assigns the I2C address of the light sensor. ``0x29 (41)`` is the default for the Grove sensor. The Adafruit version has a default of ``0x39 (57)``.

    .. method:: LightSensor.get_lux()

        Returns the light intensity reading as lux.

        .. hint::

            Useful lux values:

            * Sunlight: 107,527
            * Full Daylight: 10,752
            * Overcast Day: 1,075
            * Very Dark Day: 107
            * Twilight: 10.8
            * Full Moon: .108

    .. method:: LightSensor.show_data(screen, line)

        Shows the light intensity reading in lux on the specified ``screen`` object on the specified ``line``. Also returns the same lux reading to avoid repeated reading on the sensor.

Example
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    # The following code reads light value every 5 seconds,
    # and if it's too dark (lux < 100), prints a warning message

    from sensors import LightSensor
    import time

    l = LightSensor()

    while True:
        lux = l.get_lux()

        if lux < 100:
            print("Too Dark!")

        time.sleep(20) # wait for 20 seconds

.. _moisture_sensor:

Moisture Sensor
------------------------------

.. image:: https://github.com/SeeedDocument/Grove_Moisture_Sensor/raw/master/images/Moisture_sensor_.jpg
    :width: 200px
    :height: 200px

.. class:: sensors.MoistureSensor(port[=4])

    Allows reading moisture values from the Grove Moisture Sensor. The ``port`` parameter cannot be any other number than 4, because the sensor is analog.

    .. method:: MoistureSensor.get_moisture(port[=4])

        Returns the raw moisture reading.

        .. warning::

            Because the moisture sensor is analog, the values of the sensor readings might vary from case to case.  It is a good idea to calibrate the sensor by experimenting on the soil.

    .. method:: MoistureSensor.show_data(screen, line)

        Shows the raw moisture reading on the specified ``screen`` object on the specified ``line``.  Also returns the same raw moisture reading to avoid repeated reading on the sensor.