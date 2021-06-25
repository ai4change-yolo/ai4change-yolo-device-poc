AI4Change Yolo Device
=============================
It this repository you will find the code used directly on Rapsberry Pi with a Intel Movidius Neural Stick. For the backend/cloud component of the solution, see ai4change-yolo-backend repository.

The workflow of the solution is following:

1. RaspberryPi and Intel Movidius are used to recognize an item seen by a camera.

2. The name of recognized item is sent to AWS via MQTT (using "products" topic).

3. On AWS the recommendation is generated (using AWS Lambda).

4. The recommendation is sent back to RaspberryPi via MQTT (using "advice" topic).

5. Based on the reciveded recommendation, the image is displayed on the screen.

For deployment instructions see below.

.. image:: https://github.com/ai4change-yolo/ai4change-yolo-device/blob/master/_graphics/img1.jpg
.. image:: https://github.com/ai4change-yolo/ai4change-yolo-device/blob/master/_graphics/img2.jpg

Install needed python libraries (from pip)
________________


.. code-block:: sh

    pip install AWSIoTPythonSDK
    pip install configparser
    pip install imutils
    pip install picamera
    pip install opencv-python


Install Movidius SDK (as root)
________________


.. code-block:: sh

    mkdir -p ~/movidius

    cd ~/movidius

    wget https://ncs-forum-uploads.s3.amazonaws.com/ncsdk/ncsdk-01_12_00_01-full/ncsdk-1.12.00.01.tar.gz

    tar xzf ncsdk-1.12.00.01.tar.gz

    cd ncsdk-1.12.00.01

    make install

    make examples


Troubleshooting
________________


If error while example compilation:

*RuntimeError: module compiled against API version 0xb but this version of numpy is 0xa*

Upgrade numpy package:

.. code-block:: sh

    pip3 install --upgrade numpy


Links
________________


AWK IoT Python SDK: https://github.com/aws/aws-iot-device-sdk-python

Movidius SDK: https://developer.movidius.com/start

Real-time object detection on the Raspberry Pi with the Movidius NCS: https://www.pyimagesearch.com/2018/02/19/real-time-object-detection-on-the-raspberry-pi-with-the-movidius-ncs/

Deploying Your Customized Caffe Models on Intel® Movidius™ Neural Compute Stick: https://movidius.github.io/blog/deploying-custom-caffe-models/

Requirements
________________


absl-py==0.5.0
astor==0.7.1
AWSIoTPythonSDK==1.4.0
cloudpickle==0.5.6
cycler==0.10.0
Cython==0.28.5
-e git+https://github.com/thtrieu/darkflow.git@b2aee0000cd2a956b9f1de6dbfef94d53158b7d8#egg=darkflow
dask==0.19.2
decorator==4.3.0
gast==0.2.0
graphviz==0.9
grpcio==1.15.0
kiwisolver==1.0.1
Markdown==3.0.1
matplotlib==3.0.0
networkx==2.2
numpy==1.15.2
opencv-contrib-python==3.4.3.18
opencv-python==3.4.3.18
picamera==1.13
Pillow
protobuf==3.6.1
pygraphviz==1.5
pyparsing==2.2.1
python-dateutil==2.7.3
PyWavelets==1.0.1
PyYAML==3.13
scikit-image==0.14.0
scipy==1.1.0
six==1.11.0
tensorboard==1.9.0
tensorflow>=1.9.0
termcolor==1.1.0
toolz==0.9.0
Werkzeug
