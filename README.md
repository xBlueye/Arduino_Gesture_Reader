# Arduino_Gesture_Reader

# Hardware Requirements
- Arduino nano 33 BLE Sense
- micro-usb cable with data bus
- Laptop or PC
# Software Requirements
- Arduino IDE

# Installation
- Install Arduino IDE using this link https://www.arduino.cc/en/software .
- Run Arduino IDE.
- Go to Tools>Board>Board Manager
- Install Arduino Mbed OS Nano Boards to detect BLE Sense.
- Go to Tools>Manage Libraries
- Install the following libraries to utilize all the sensors on BLE Sense: Arduino_HTS221, Arduino_LPS22HB, Arduino_LSM9DS1, Arduino_TensorFlowLite, ArduinoBLE, ArduinoSound and JPEGDecoder
- Download the ArduinoSketches folder and place it in C:\Users\ <user> \Documents\Arduino\libraries\
- Create a new folder on your desktop to store data.
# Usage
- Connect the BLE Sense using a micro-usb cable to your laptop/PC.
- Go to Tools>Board>Arduino Mbed OS Nano Boards>Arduino Nano 33 BLE
- Go to Tools>Port> <USB port connected with your board>
- Open IMU_Capture from ArduinoSketches in your IDE.
- Run the program and wait untill it's compiled.
- Open the serial monitor. (Right upper corner)
- You'll know if the program runs if you see aX	aY	aZ	gX	gY	gZ  on the serial monitor.
- You can now start creating a dataset with your gestures. Hold onto the arduino and repeat a gesture of your choice to create a dataset (atleast 30 samples per gesture.)
- After every gesture you make you should see the data from the accelerometer and gyroscpoe in the serial monitor. (You can change the sensitivity of the program with this variable: const float accelerationThreshold )
- If you think you have enough data copy everything from the serial monitor , top line aswell , and save it as a csv file in your data folder as <gesture>.csv
- To read another gesture , close the serial monitor and restart the arduino with the reset button. Open the serial monitor and make sure the aX	aY	aZ	gX	gY	gZ line is present.
- If you think you have enough data, close the IDE and go to this notebook https://colab.research.google.com/github/arduino/ArduinoTensorFlowLiteTutorials/blob/master/GestureToEmoji/arduino_tinyml_workshop.ipynb
- Change !pip install tensorflow==2.0.0-rc1 in the first code block to !pip install tensorflow==2.8.0 (2.0.0-rc1 is depricated)
- In the third code block file GESTURES list with all the gestures you have a dataset for.
- On the left side , click the folder icon(files) and upload all your csv files.
- Run all code blocks from top to bottom.
- If the accuracy of your model isn't good or satisfying it means your data was inconsitant( bad readings, lack of variety or inconsitant movements/accidental readings due to too high sensitivity) or there weren't enough samples per gesture.(the more gestures you have the more samples each gesture should have) Redo your datasets and try again.
- Wait until the files refresh or do it manually with the second button under files.
- You should see model.h file appear , hover over it > click the 3 dots > download and save it in C:\Users\gebruiker\Documents\Arduino\libraries\ArduinoSketches\IMU_Classifier\model.h
- Now open IMU_Classifier in Arduino IDE
- Change the accelerationThreshold to whatever you used in Capture, scroll down until you see GESTURES[] and fill it with your gestures.
- Again : connect your arduino , select board and port , compile the program , open the serial monitor and you should be ready to go.
 
