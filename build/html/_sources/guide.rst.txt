.. _quickstart:

Quickstart Guide
=================================

The Wio Link board designed by `SeeedStudio <http://seeedstudio.com>`_ makes it easier to connect sensors and other electronic devices to the board with the Grove interface. We define six grove `ports` numbered below:

.. image:: ports.png

To get started with programming with MicroPython on the Wio Link board, first make sure that you have the firmware installed on the board following the :ref:`wiolink` guide. Then, in the EsPy IDE, connect to the board by clicking on the "Connect" button on the toolbar. Reset the board by pressing the "reset" button on the board, hitting ``Ctrl+D``, or clicking the ``Reset`` button on the toolbar. You will then see a ``>>>`` prompt in the terminal window at the bottom of the screen.

Programming the electronic devices follows the following rules: first you need to create an ``instance`` of that device.  This can usually be done in three simple steps:

1. Import the corresponding class
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Let us use the :ref:`temp_sensor` connected to Port 3 as an example.  The syntax is follows:

>>> from sensors import TemperatureSensor

``from`` and ``import`` are Python reserved words. :mod:`sensors` is the name of the module, which is always in lowercase ending with an "s." There are three modules available: :mod:`sensors`, :mod:`actuators`, and :mod:`displays`. Within each module you will find the classes available for your device. Refer to the table below to locate your class, which is always in `CamelCase <https://en.wikipedia.org/wiki/Camel_case>`_.

2. Create an instance referring to the sensor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create an instance of the ``TemperatureSensor`` class referring to the sensor at Port 3 like this:

>>> temp_sensor = TemperatureSensor(3)

or 

>>> temp_sensor = TemperatureSensor(Port=3)

Each device has a default port, and if the sensor is already connected at its default port, then there is no need to specify port number. There might be additional arguments/parameters when creating the instance. Please refer to the :ref:`api` for more information.

3. Interact with the devices using the instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Each class offers a set of functionalities for interacting with the devices. In this case, the ``TemperatureSensor`` class offers ``TemperatureSensor.get_temperature()`` and ``TemperatureSensor.get_humidity()`` methods. To use these methods, simply use the **dot notation** to access the methods:

>>> temp_sensor.get_temperature()
>>> temp_sensor.get_humidity()

Please refer to the :ref:`api` for more information on how to use these classes.