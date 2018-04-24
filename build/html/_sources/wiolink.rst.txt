.. _wiolink:

Setting up WioLink boards
====================================

.. image:: ports.png

System Requirement
------------------------------------

We recommend Windows PCs for development because the excellent `EsPy` integrated development environment (IDE) runs only on Windows. If you are running MacOS or Linux operating systems, there are other IDEs available, such as `uPyCraft <https://legacy.gitbook.com/book/dfrobot/upycraft/details>`_ (for Windows and Mac) and `ESPlorer <https://github.com/4refr0nt/ESPlorer>`_ (written in Java, runs on all platforms), but they do not offer as comprehensive functionalities as does `EsPy`, such as a file system viewer that allows you to see the files on your WioLink board.

In order to run EsPy, make sure you have the following installed:

* Microsoft .net Framework (already installed if you have Windows 10) (`Download <https://www.microsoft.com/net/download/dotnet-framework-runtime>`_)
* Python 3.5+ (`Download <https://www.python.org/downloads/>`_)

Downloading EsPy IDE
------------------------------------

Go to `this page <https://github.com/jungervin/EsPy/tree/master/EsPy/Release>`_ and download the latest version of EsPy (1.0.0.12 as of Apr. 23, 2018). You might need `7-Zip <https://www.7-zip.org/>`_ to work with the .7z archives. You can put the extracted folder anywhere in your system.

Downloading MicroPython Firmware
------------------------------------

`Click here <https://github.com/digicosmos86/wiolink/raw/master/micropython-1.9.3-wiolink-clean.bin>`_ to download the MicroPython firmware

Flashing MicroPython Firmware
------------------------------------

If you are using the `EsPy` IDE, you can use it to flash the downloaded firmware to the WioLink board with the following steps:

1. Download :mod:`esptool` package
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Go to `this page <https://github.com/espressif/esptool>`_ and click on the green "Clone or Download" button, and choose "Download ZIP". Extract the downloaded zip file to a folder in your system.

.. image:: https://sebastiansauer.github.io/images/2016-10-12/download_repo.png

2. Install :mod:`PySerial` package
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Press `Win+R` (Press `Windows` key and `R` key at the same time). In the "Run..." dialog box that pops up, type cmd, and hit enter. In the command console window that shows up, run ``pip install pyserial`` command to install the :mod:`PySerial` package, which :mod:``esptool`` requires.

3. Put the WioLink board to Flash mode and connect it to the computer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Install the CP2012 driver for your system `here <https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers>`_. Hold the config button on the WioLink board and connect it to your computer.

4. Flash the firmware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Open the EsPy program. First, go to "Device"->"Ports"->"COMx" where ``x`` could be any number. Make sure the ``COMx`` is selected. Then, go to "Device"->'EspTool...".

In the Dialog that opens subsequently (shown below), make sure "Serial Port" is the one that you saw in the "Ports" menu. Leave "Baud Rate" and "Python.exe" as default. Use the ".." button on the same line as "esptool.py" to find the ``esptool.py`` in the esptool folder that you have just extracted . Use the ".." button on the same line as "firmware.bin" to locate the firmware file that you have just downloaded. Leave everything else to default values.

Click the "1. Erase" button first.  After the old firmware is successfully erased, flash the new firmware by clicking the "2. Write" button.

.. image:: https://raw.githubusercontent.com/jungervin/EsPy/master/EsPy/Helps/images/esptool.png

Testing Installation
------------------------------------

Click on the "Reset" button on the board to reset the board. If the red LED comes on, then you have flashed your firmware correctly. If not, repeat the 3rd and 4th steps above.