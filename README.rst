Subsonic IPT
============

An Arduino sketch for inertial position tracking using an MPU6060 accelerometer and gyroscope.

This repository was developed by the "Subsonic" team as part of an assignment for the courses GE 1501 and GE 1502 at Northeastern University during Fall 2019 and Spring 2020, respectively.

This codebase consists of Arduino-C++, which is a dialect of C++ that notably does not link against the C++ standard library.

See `this diagram`_ for how to wire this project. This image was created with `Fritzing`_.

.. _this diagram: ./resources/ipt_fritzing_diagram_v2.0.0.png
.. _Fritzing: https://fritzing.org/home/

Installation
------------

To install the latest release of this sketch, simply clone the git repository by running

.. code-block:: shell

    $ git clone https://github.com/blueschu/Subsonic-IPT.git

This sketch depends on the `SparkFun SerLCD library`_. If you have not previously installed this library, you can install if by following the steps outlined in the `SparkFun tutorial`_ for installing Arduino libraries.

.. _SparkFun SerLCD library: https://github.com/sparkfun/SparkFun_SerLCD_Arduino_Library
.. _SparkFun tutorial: https://learn.sparkfun.com/tutorials/installing-an-arduino-library

This sketch makes use of some C++17 language features, such as inline variables. Therefore, it is recommended that you configure your arduino installation to pass the appropriate language flag to the compiler. This can be accomplished by editing the ``platform.txt`` file contained in your Arduino installation directory. On Linux, this file is located at ``<arduino install directory>/hardware/arduino/avr/platform.txt``. Within this file, navigate to the ``compiler.cpp.flags=`` setting and replace ``-std=gnu++11`` with ``-std=gnu++1z``.

Running the Sketch
------------------

This repository is designed to be built and run using CMake. However, it is still possible to run this sketch using the Arduino IDE.

Running with CMake
^^^^^^^^^^^^^^^^^^

First, ensure that you have ``cmake`` installed on your system. If you are using an IDE such as `CLion`_, ``cmake`` would have been included with your installation.

Next, update the ``arduino-variables.cmake`` file to reflect your local Arduino installation. The file included in this repository represents an Arduino v1.8.10 installation in ``/opt`` on a Linux system. If you are using an operating system other than Linux, you may need to look up the appropriate system paths for your Arduino installation. For MacOS users, you may find the `arduino-clion-minimal`_ repository which inspired the structure of this repository helpful.

If you are using `CLion`_, follow the steps given in `this blog post`_ to configure your IDE's toolchain.

.. _arduino-clion-minimal: https://github.com/cpbotha/arduino-clion-minimal
.. _this blog post: https://vxlabs.com/2018/03/24/developing-arduino-sketches-with-jetbrains-clion-a-minimal-example/
.. _CLion: https://www.jetbrains.com/clion/

Otherwise, you can build the project manually with `cmake` by running the following commands:

.. code-block:: shell

    $ mkdir cmake-build-debug
    $ cd !$
    $ cmake -DCMAKE_TOOLCHAIN_FILE=arduino-uno-toolchain.cmake ..

To build the sketch, run the ``verify`` CMake target.
To upload the sketch to your Arduino, run the ``upload`` CMake target.

Running with the Arduino IDE
------------------------

To run this sketch using the Arduino IDE, rename the ``sketch.cpp`` file to have an ``.ino`` extension. Then, open this repository as you would any other Arduino sketch.


Credits
-------

The Arduino/CMake integration used in this repository is a custom Linux port of a template created by Charl P. Botha. His original ``arduino-clion-minimal`` repository may be found `here`_.

.. _here: https://github.com/cpbotha/arduino-clion-minimal

License
-------

This software is licensed under the `MIT License`_. For more
information, read the file `LICENSE`_.

.. _MIT License: https://opensource.org/licenses/MIT
.. _LICENSE: ./LICENSE
