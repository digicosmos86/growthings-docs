.. _wiolink:

Setting up WioLink boards
====================================

.. image:: ports.png

System Requirement
------------------------------------

We recommend Windows PCs for development because the excellent `EsPy` integrated development environment (IDE) runs only on Windows. If you are running MacOS or Linux operating systems, there are other IDEs available, such as `uPyCraft <https://legacy.gitbook.com/book/dfrobot/upycraft/details>`_ (for Windows and Mac) and `ESPlorer <https://github.com/4refr0nt/ESPlorer>`_ (written in Java, runs on all platforms), but they do not offer as comprehensive functionalities as does `EsPy`, such as a file system viewer that allows you to see the files on your WioLink board.

.. tip:: Organizing your downloaded files

    We will be downloading a lot of files. It is a good idea to put everything you have downloaded into one folder (e.g. Downloads), and create a new folder (e.g. on your desktop called "MicroPython") to organize all your extracted files.

In order to run `EsPy`, make sure you have the following installed:

.. rubric:: Download Links:

* `CP2012 USB to UART Controller Driver <https://www.silabs.com/documents/public/software/CP210x_Windows_Drivers.zip>`_
* `Microsoft .net Framework (Required for Windows 7, 8, 8.1, Optional for Windows 10) <https://www.microsoft.com/net/download/dotnet-framework-runtime>`_
* `Python 3 <https://www.python.org/downloads/>`_
* `7-Zip Archive Manager <https://www.7-zip.org/>`_

.. note:: Installing Python

    Any version of Python 3 will work (Python 2 will not work in this case).  Make sure you check "Add Python to PATH" option when installing Python 3:

    .. image:: https://i.stack.imgur.com/CCXQG.jpg

Downloading EsPy IDE
------------------------------------

Use the following link to download the latest version of EsPy (1.0.0.12 as of Apr. 23, 2018). The 7-Zip Archive Manager that you have just installed can be used to work with the downloaded 7z file. Double-click on the file and extract the "Release" folder to the "MicroPython" folder that you have just created. Feel free to rename the "Release" folder to "EsPy" if you wish.

.. rubric:: Download Links:

* `EsPy IDE <https://github.com/jungervin/EsPy/tree/master/EsPy/Release>`_

Downloading MicroPython Firmware
------------------------------------

Use the following link to download the custom MicroPython firmware for the WioLink boards. 

.. rubric:: Download Links:

* `Custom MicroPython Firmware for WioLink boards <https://github.com/digicosmos86/wiolink/raw/master/micropython-1.9.3-wiolink-clean.bin>`_

Flashing MicroPython Firmware
------------------------------------

The EsPy IDE comes with an excellent GUI for flashing the firmware you have just downloaded. You can use it to flash the downloaded firmware to the WioLink board with the following steps:

1. Install the :mod:`esptool` package with :mod:`pip`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Press `Win+R` (Press `Windows` key and `R` key at the same time). In the "Run..." dialog box that pops up, type cmd, and hit enter. In the command console window that shows up, type the following command and hit enter:

.. image:: https://www.isunshare.com/images/article/windows-8/hide-or-unhide-files-and-folders-with-command-prompt/input-cmd-and-click-ok.png

.. code-block:: bash

    pip install esptool

That will install :mod:`esptool` to your Python and all its dependencies.

.. tip:: ``pip`` not found?

    If you see the "pip not found" after using the command, try uninstalling Python 3 and reinstall it. This time, make sure "Add Python to PATH" is selected.

    .. image:: https://i.stack.imgur.com/CCXQG.jpg

2. Put the WioLink board to Flash mode and connect it to the computer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you haven't already, use the following link to install the CP2012 driver for your system. Next, hold the config button on the WioLink board (the one to the left of the MicroUSB port) and connect it to your computer.

.. rubric:: Download Links:

* `CP2012 USB to UART Controller Driver <https://www.silabs.com/documents/public/software/CP210x_Windows_Drivers.zip>`_

3. Flash the firmware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Open the EsPy program. It should be in a folder called "EsPy" or "Release" in the "MicroPython" folder on your desktop.

Go to "Device"->"Ports"->"COMx" where ``x`` could be any number. Make sure the ``COMx`` is selected. Then, go to "Device"->'EspTool...".

In the Dialog that opens subsequently (shown below), make sure "Serial Port" is the one that you saw in the "Ports" menu. Leave "Baud Rate", "Python.exe", and "esptool.py" as default. Use the ".." button on the same line as "firmware.bin" to locate the firmware file (micropython-1.9.3-wiolink-clean.bin) that you have just downloaded. Leave everything else to default values.

Click the "1. Erase" button first.  After the old firmware is successfully erased, flash the new firmware by clicking the "2. Write" button.

.. image:: https://raw.githubusercontent.com/jungervin/EsPy/master/EsPy/Helps/images/esptool.png

Testing Installation
------------------------------------

Close the EspTool dialog and click on the "Reset" button on the board to reset the board. Click the "Connect" button on the toolbar of EsPy. If you see something like:

.. code-block:: bash

    Press Ctrl+D to do a software reset
    Press Ctrl+I to interrupt the current program

Congratulations! You are ready to program your WioLink board.