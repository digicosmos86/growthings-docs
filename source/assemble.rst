Assembling the Smart Greenhouse
====================================

Assembling the smart greenhouse is very simple. Use the following two steps:

Step 1. Hardware Assembly:
------------------------------------

You will need these devices connected to the following ports:

* A :ref:`relay`: Connected to Port 1
* A :ref:`servo`: Connected to Port 2
* A :ref:`temp_sensor_pro`: Connected to Port 3
* An :ref:`grow_light`: Connected to Port 5
* An I2C hub or branch cable: Connected to Port 6
* An :ref:`oled`: Connected to the I2C hub or branch cable
* A :ref:`light_sensor`: Connected to the I2C hub or branch cable

Step 2. Software installation:
------------------------------------

Use the following link to download `main.py`. Use EsPy's file manager to upload the file to the WioLink board. Alternatively, you can copy the code below and create a new file called `main.py` in EsPy. Save the file and use the upload button to upload it to the WioLink board. Either way, when you are finished, simply press the reset button. The board should start to work after 5 seconds.

.. rubric:: Download Links:

* `main.py <https://raw.githubusercontent.com/digicosmos86/wiolink/master/main.py>`_