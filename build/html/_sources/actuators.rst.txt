:mod:`actuators` - Working with Actuators
=========================================

The :mod:`actuators` module provides a collection of classes to interact with actuators, such as servos, relays, and buttons.

.. _servo:

Servo
----------------------------------

.. image:: https://github.com/SeeedDocument/Grove-Servo/raw/master/img/Grove%E2%80%94Servo.jpg
    :width: 200px
    :height: 200px

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

.. _relay:

Relay
----------------------------------

.. image:: https://raw.githubusercontent.com/SeeedDocument/Grove-Relay/master/img/Twig-Relay.jpg
    :width: 200px
    :height: 200px

.. class:: actuators.Relay(port[=1])

    Allows control of a Grove Relay. The relay by default is normally open (NO) triggered by a ``high`` signal.

    .. method:: Relay.on()

        Activate the relay, close the circuit, and turn on whatever appliance that's connected to the relay.

    .. method:: Relay.off()

        Deactivate the relay, open the circuit, and turn off whatever appliance that's connected to the relay.

    .. method:: Relay.is_on()

        Returns ``True`` if the relay is on, or ``False`` if the relay is off.

.. _button:

Button
-------------------------

.. image:: https://github.com/SeeedDocument/Grove_Button/raw/master/img/Button.jpg
    :width: 200px
    :height: 200px

.. class:: actuators.Button(port[=2], pullup[=True])

    Allows control of a Grove Button.  There are two ways to use a button.  First, you can access ``Button.is_pressed`` property or ``Button.is_pressed()`` method to determine if the button is pressed.  Alternatively, you can also set a callback function with ``Button.on_release()`` method use the interrupt mechanism.  Please see example of how to use the callback.

    .. method:: Button.is_pressed()

        Returns ``True`` if the button is pressed, or ``False`` if it is not.

    .. method:: Button.on_press(callback)

        Executes the ``callback`` function provided to the method when the button is pressed.

    .. method:: Button.on_release(callback)

        Executes the ``callback`` function provided to the method when the button is released.

Example
^^^^^^^^^^^^^^^^^^^^^

Controlling the LED with the Button

.. code-block:: python

    from actuators import Led, Button
    led = Led(1) # Specifies an LED at Port 1
    button = Button(2) # Specifies a button at Port 2

    ## Turns on the LED when the button is pressed

    while True:

        if button.is_pressed():
            led.on()
        else:
            led.off()

Turns the LED on/off with a callback function

.. code-block:: python

    from actuators import Button
    from displays import Led
    led = Led(1, on=False) # Specifies an LED at Port 1
    button = Button(2) # Specifies a button at Port 2

    ## Define a callback function

    def turn_on_led(pin):
        global led # Need this line to refer to the led object outside the function.

        if led.is_on():
            led.off()
        else:
            led.on()

    ## Set the callback function to Button.on_release method.

    button.on_release(callback=turn_on_led) # Note that no () are needed.