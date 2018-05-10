:mod:`iot` Connecting with Other Devices
===========================================

The :mod:`iot` module provides a collection of classes to connect to WiFi and exchange data with other devices, such as Raspberry Pis.

.. _wifi:

WiFi
--------------------------------

This class can be used to connect the Wio Link board to WiFi.

.. class:: iot.WiFi(ssid, password)

    Stores the WiFi ``ssid`` and ``password``, so when the ``connect()`` method is called, the Wio Link board will connect to the specified WiFi ``ssid`` with the ``password``.

    .. note::

        After WiFi is successfully connected, the Wio Link board will attempt to access the same WiFi at each subsequent boot. You can click the "Soft Reset" button to get the terminal to work again.

    .. method:: WiFi.connect()

        When the ``connect()`` method is called, the Wio Link board will connect to the specified WiFi ``ssid`` with the ``password`` specified when object is created.

Example:
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    # Connects to a WiFi access point
    # with SSID starbucks
    # and Password 12345678

    from iot import WiFi
    wifi = WiFi(ssid="starbucks", password="12345678")
    wifi.connect()

.. _nodered:

Node-RED
--------------------------------

This class can be used to send data to any device that runs Node-RED, such as Raspberry Pis, or even a Node-RED instance running on the cloud, provided the IP address of the hosting machine is known.

.. class:: iot.NodeRed(ip, [port=1880])

    Stores the ``ip`` address of the machine running Node-RED. If Node-RED runs on a different ``port`` than ``1880``, the ``port`` parameter can be used to specify the port.

    .. method:: NodeRed.send_http(url, data)

        Send the specified ``data`` to the http-in node in the Node-RED flow. the ``url`` parameter needs to be exactly the same as the ``URL`` field of the http-in node (shown below). ``data`` can either be a number, a string, or a dictionary.

        .. image:: node_red_http.png

Example:
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    # Connects to a WiFi access point
    # with SSID starbucks
    # and Password 12345678

    from iot import WiFi, NodeRed
    from sensors import TemperatureSensor
    import time

    wifi = WiFi(ssid="starbucks", password="12345678")
    wifi.connect()

    # Temperature Sensor is connected to Port 3
    temp_sensor = TemperatureSensor(3)

    # Node-RED is hosted on a machine with IP 192.168.1.123
    # It has a http in node configured with URL /test

    node = NodeRed(ip="192.168.1.123")

    # Sends temperature and humidity data to Node-RED every 10 seconds

    while True:
        t = temp_sensor.get_temperature()
        h = temp_sensor.get_humidity()

        data_dict = {
            "temperature": t,
            "humidity": h
        }

        node.send_http(url="/test", data=data_dict)
        time.sleep(10)