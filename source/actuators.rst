Actuators
==================================

Servo
----------------------------------

.. class:: actuators.Servo(port[=2], position[=0])

    Allows control of a Grove Servo. Default ``port`` for the servo is ``2``. The ``position`` parameter sets the initial position of the servo.

    .. method:: Servo.set_position(degree)

        Sets the ``degree`` position of the servo (between ``0`` and ``180``, which is half a circle). If ``degree`` is greater than 180, the servo will be set at the ``180`` degree position.  Likewise, if ``degree`` is less than ``0``, the servo will rotate to the 0 degree position.

    .. method:: Servo.get_position()

        Returns the current position of the servo in degrees.

Example:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    from actuators import Servo

    s = Servo(1, init_degree = 180) # defines a servo connected to port 1 with initial position at 180 degrees.
    s.set_position(90) # rotate the servo by 90 degrees.

Relay
----------------------------------

.. class:: actuators.Relay(port[=1])

    Allows control of a Grove Relay. The relay by default is normally open (NO) triggered by a ``high`` signal.

    .. method:: Relay.on()

        Activate the relay, close the circuit, and turn on whatever appliance that's connected to the relay.

    .. method:: Relay.off()

        Deactivate the relay, open the circuit, and turn off whatever appliance that's connected to the relay.

Grow Light Strip
----------------------------------

.. class:: GrowLight(port[=1], n[=60])

    Allows control of a 5V LED strip based on the WS2812b (NeoPixel). ``n`` specifies the number of LEDs on the strip. Default is ``60``.

    .. method:: GrowLight.on()

        Turns on the LED strip as a plant growth light that emits red and blue light.

    .. method:: GrowLight.off()

        Turns off the LED strip.

    .. hint::

        This class is a subclass of MicroPython's ``neopixel.NeoPixel`` class, so it can be programmed the same way as the Neo Pixel.  See `this page <http://docs.micropython.org/en/latest/esp8266/esp8266/tutorial/neopixel.html>`_ for more details and examples.