# BTS_Camera
## RPI Command Code
### Download and Update1 & Testing
~~~
sudo apt update
sudo apt full-upgrade
sudo apt-get update
sudo apt-get dist-upgrade

#Camera
sudo raspi-config 
raspistill -v -o test.jpg
raspivid -v -t 10000 -o testvid.h264

#Tensorflow Lite script download
git clone https://github.com/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi.git
~~~

### Download and Update2
~~~
#Install OpenCV, TensorflowLite_files
sudo pip3 install opencv-python 
bash get_pi_requirements.sh

##Download and Install TPU files
echo "deb https://packages.cloud.google.com/apt coral-edgetpu-stable main" | sudo tee /etc/apt/sources.list.d/coral-edgetpu.list
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
sudo apt-get update
sudo apt-get install libedgetpu1-std
~~~


### Virtual envrionment Run1
~~~
#Tensorflow Lite Virtual environment setting
mv TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi tflite1
cd tflite1
sudo pip3 install virtualenv
python3 -m venv tflite1-env
source tflite1-env/bin/activate

sudo pip3 install pandas
#Ultrasonic sensor
sudo pip3 install wiringpi2
#Servo
sudo pip3 install gpiozero
sudo pip3 install pigpio
sudo pigpiod
~~~

### Run2(after putting tflite files into a folder) 
~~~
##Tensorflow Lite webcam code with TPU
python3 TFLite_detection_webcam.py --modeldir=Sample_TFLite_model --edgetpu

#Tensorflow Lite webcam code without TPU
python3 TFLite_detection_webcam.py --modeldir=Sample_TFLite_model
~~~
