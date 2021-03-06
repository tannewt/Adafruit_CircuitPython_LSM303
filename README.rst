
Introduction
============

.. image:: https://readthedocs.org/projects/adafruit-circuitpython-lsm303/badge/?version=latest
    :target: https://circuitpython.readthedocs.io/projects/lsm303/en/latest/
    :alt: Documentation Status

.. image :: https://img.shields.io/discord/327254708534116352.svg
    :target: https://discord.gg/nBQh6qu
    :alt: Discord

Adafruit CircuitPython module for the LSM303 6-DoF with 3-axis accelerometer and magnetometer

Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_
* `Bus Device <https://github.com/adafruit/Adafruit_CircuitPython_BusDevice>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://github.com/adafruit/Adafruit_CircuitPython_Bundle>`_.

Usage Example
=============

.. code-block:: python
                
	import time
	import board
	import busio

	import adafruit_lsm303

	i2c = busio.I2C(board.SCL, board.SDA)
	sensor = adafruit_lsm303.LSM303(i2c)

	while True:
		raw_accel_x, raw_accel_y, raw_accel_z = sensor.raw_accelerometer
		accel_x, accel_y, accel_z = sensor.accelerometer
		raw_mag_x, raw_mag_y, raw_mag_z = sensor.raw_magnetometer
		mag_x, mag_y, mag_z = sensor.magnetometer

		print('Acceleration raw: ({0:6d}, {1:6d}, {2:6d}), (m/s^2): ({3:10.3f}, {4:10.3f}, {5:10.3f})'.format(raw_accel_x, raw_accel_y, raw_accel_z, accel_x, accel_y, accel_z))
		print('Magnetometer raw: ({0:6d}, {1:6d}, {2:6d}), (gauss): ({3:10.3f}, {4:10.3f}, {5:10.3f})'.format(raw_mag_x, raw_mag_y, raw_mag_z, mag_x, mag_y, mag_z))
		print('')
		time.sleep(1.0)


API Reference
=============

.. toctree::
   :maxdepth: 2

   api

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_LSM303/blob/master/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.

Building locally
================

To build this library locally you'll need to install the
`circuitpython-build-tools <https://github.com/adafruit/circuitpython-build-tools>`_ package.

.. code-block:: shell

    python3 -m venv .env
    source .env/bin/activate
    pip install circuitpython-build-tools

Once installed, make sure you are in the virtual environment:

.. code-block:: shell

    source .env/bin/activate

Then run the build:

.. code-block:: shell

    circuitpython-build-bundles --filename_prefix adafruit-circuitpython-lsm303 --library_location .
