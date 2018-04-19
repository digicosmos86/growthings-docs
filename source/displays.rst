`displays` - Working with Displays
====================================

The :mod:`displays` module provides a collection of classes to interact with screens. As of now only the Grove 0.96" OLED screen is supported.

OLED Screen
----------------------------------

.. class:: screens.OledScreen(port[=6], width[=128], height[=64], address[=0x3c])

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

        Writes the data on the specified ``sensor`` to the specified ``line``.

Example:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    from displays import OledScreen

    screen = OledScreen(6)
    screen.show_line(1, "Hello World!")