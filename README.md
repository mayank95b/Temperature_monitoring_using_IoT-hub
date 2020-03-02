# Temparature and Humidity Monitoring System on Azure IoT-hub
Monitoring Temperature and Humidity data on Azure IoT hub in real time.

### Overview of DHT11 Sensor:

The DHT11 sensor can measure relative humidity and temperature with the following specifications:

Temperature Range: 0-50°C

Temperature Accuracy: ±2 °C

Humidity Range: 20-90% RH

Humidity Accuracy: ±5 %

### How DHT11 Sensor works:

The DHT11 sensor comes with a blue or white colour casing. Inside this casing we have two important componentswhich help us to sense the relative humidity and temperature. The first component is a pair of electrodes; the electrical resistance between these two electrodes is decided by a moisture holding substrate. So the measured resistance is inversely proportional to the relative humidity of the environment. Higher the relative humidity lower will be the value of resistance and vice versa.  Also note that Relative humidity is different from actual humidity. Relative humidity measures the water content in air relative to the temperature in the air.
The other component is a surface mounted NTC Thermistor. The term NTC stands for Negative temperature coefficient, for increase in temperature the value of resistance will decrease

### Hardware components:

•	Raspberry Pi 3

•	DHT11 Temperature & Humidity Sensor (3 pins)

### Procedure:

- `Step1` :
Create an IoT hub

    Refer the DHT11AzureMqtt.doc for detail.

- `Step2` :
    
     Download the Python project from https://github.com/mayank95b/DHT11SensorAzure-IoT-hub-Rasp.git and extract the ZIP archive.

- `Step3` :
Installing the Adafruit DHT11 library on Raspberry Pi:

    pi@raspberrypi:~ $ git clone https://github.com/adafruit/Adafruit_Python_DHT.git 

    pi@raspberrypi:~ $ cd Adafruit_Python_DHT

    pi@raspberrypi:~ $ sudo apt-get install build-essential python-dev 

    pi@raspberrypi:~ $ sudo python setup.py install

- `Step4` :
Before continuing any further I do recommend testing the DHT11 sensor is working correctly.This can quickly be done by changing some of the lines of the file simpletest.py in the location: /Adafruit_Python_DHT/examples/

Below are the areas of the file which require changing and the values required (e.g. pin = 4) to enable the test script to work:

    uncomment the Pin=4 line and put comment in Beaglebone pin.change Dht22 to Dht11.

- `Step5` :
Now, In a local terminal window, navigate to the root folder of the Python project.
Open the Dht11Azure.py file in a text editor of your choice.

Replace the value of the CONNECTION_STRING variable with the device connection string you made a note of previously. Then save your changes to Dht11Azure.py file


- `Step6` :
In the local terminal window, run the following commands to install the required libraries for the simulated device application:

    pip install azure-iothub-device-client

- `Step7` :
In the local terminal window, run the following commands to run the DHT11 device application:

    python Dht11Azure.py

- `Step8` :
Read the telemetry from your hub

•	The IoT Hub CLI extension can connect to the service-side Events endpoint on your IoT Hub. The extension receives the device-to-cloud messages sent from your simulated device. An IoT Hub back-end application typically runs in the cloud to receive and process device-to-cloud messages.

•	Run the following commands in Azure Cloud Shell, replacing YourIoTHubName with the name of your IoT hub:

    >>az iot hub monitor-events --hub-name YourIoTHubName --device-id <urdevicename>

To avoid the import iothub_client error

The current version of the Azure IoT SDK for Python is a wrapper over our C SDK. It is generated using the Boost library. Because of that, it comes with several significant limitations. See more details here

Check that you have the right version of Python. Be aware that only certain versions works fine for this sample.

Check that you have the right version of C++ runtime Microsoft Visual C++ Redistributable for Visual Studio 2019. (We recommend the latest).

Verify that you have installed the iothub client: pip install azure-iothub-device-client.


     apt-get install libboost-python1.62.0

