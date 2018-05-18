:mod:`displays` - Working with Screens and LEDs
===============================================

The :mod:`displays` module provides a collection of classes to interact with screens, LED lights, and LED strips.

.. _oled:

OLED Screen
----------------------------------

.. image:: https://statics3.seeedstudio.com/seeed/img/2016-09/RfiiaySPfAWrtPqmFhC1Co4u.jpg
    :width: 200px
    :height: 200px

.. class:: displays.OledScreen(port[=6], width[=128], height[=64], address[=0x3c])

    Allows control of a Grove 0.96' OLED screen. It is an I2C device so it will only work on ``Port 6`` or an I2C hub that is connected to ``Port 6``. You can specify the ``width`` and ``height`` of the screen (default 128x64). You can also specify the I2C address of the screen. If you are not sure, just use default values and everything will be taken care of.

    The screen has an internal representation of the content it displays called `framebuffer`. Usually you will need to change `framebuffer` first, and call the ``show()`` method to change what is actually displayed on the screen. Some of the following methods only changes the buffer, while some directly modifies what is displayed on the screen. Please choose these methods accordingly.

    .. method:: OledScreen.clear()

        Clears the `framebuffer`. Does **NOT** change what is displayed on the screen. Please call the ``show()`` method subsequently to see the result.

    .. method:: OledScreen.clear_line(line)

        Clears the specified ``line`` in the framebuffer. Does **NOT** change what is displayed on the screen. Please call the ``show()`` method subsequently to see the result.

    .. method:: OledScreen.write_line(line, message)

        Writes the ``message`` to the specified ``line``. Does **NOT** change what is displayed on the screen. Please call the ``show()`` method subsequently to see the result.

    .. method:: OledScreen.show_line(line, message)

        Writes and shows the ``message`` to the specified ``line``. This method directly changes what is displayed on the screen.

    .. method:: OledScreen.show_sensor_data(sensor, line)

        Writes the data on the specified ``sensor`` to the specified ``line`` and returns the data readings from the sensor to avoid reading data repetitively.

Example:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    from displays import OledScreen

    screen = OledScreen(6)
    screen.show_line(1, "Hello World!")

.. _led:

LED Lights
-------------------------------------

.. image:: https://github.com/SeeedDocument/Grove-Red_LED/raw/master/img/Grove-LED_Photo.jpg
    :width: 200px
    :height: 200px

.. class:: displays.Led(port[=1], on[=True])

    Allows control of a Grove LED socket. It is possible to switch the LEDs on the socket. The LEDs have polarities. The longer leg is positive.

    .. method:: Led.on(fade[=False], duration[=1])

        Turns on the LED. If the ``fade`` parameter is set to ``True``, then the led will turn on gradually in the number of seconds set to the ``duration`` parameter.

    .. method:: Led.off(fade[=False], duration[=1])

        Turns off the LED. If the ``fade`` parameter is set to ``True``, then the led will turn off gradually in the number of seconds set to the ``duration`` parameter.

    .. method:: Led.is_on()

        Returns ``True`` if the LED is on, or ``False`` if it is off.

.. _grow_light:

Grow Light Strip
----------------------------------

.. image:: https://statics3.seeedstudio.com/product/30led%20Strip_02.jpg
    :width: 200px
    :height: 200px

.. class:: displays.GrowLight(port[=1], n[=60], on[=True])

    Allows control of a 5V LED strip based on the WS2812b (NeoPixel). ``n`` specifies the number of LEDs on the strip. Default is ``60``. If ``on`` is set to ``True`` then the GrowLight will automatically turn on.

    .. method:: GrowLight.on()

        Turns on the LED strip as a plant growth light that emits red and blue light.

    .. method:: GrowLight.off()

        Turns off the LED strip.

    .. method:: GrowLight.is_on()

        Returns ``True`` if the grow light is on, or ``False`` if it is off.

    .. method:: GrowLight.blink(color[=255, 255, 255]], times[=3], interval[=0.5])

        Makes the LED strip blink. You can specify the ``color`` and ``times`` it blinks. ``color`` is a list or a tuple of ``R``, ``G``, ``B`` values, with intensity that goes from ``0`` to ``255``. For example, ``[255, 0, 0]`` sets the LED strip to red at its maximum intensity. Use ``interval`` to control how long each blink lasts.

    .. method:: GrowLight.demo(program[="cycle"])

        Demonstrates 3 different animations on the LED strip.  The default program is ``"cycle"``. Also available are ``"bounce"`` and ``"fade"``. Try them out!

    .. hint::

        This class is a subclass of MicroPython's ``neopixel.NeoPixel`` class, so it can be programmed the same way as the Neo Pixel.  See `this page <http://docs.micropython.org/en/latest/esp8266/esp8266/tutorial/neopixel.html>`_ for more details and examples.