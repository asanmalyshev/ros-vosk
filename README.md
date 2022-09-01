ros_vosk
======================

A ROS package for speech-to-text services based on [Vosk](https://github.com/alphacep/vosk-api)

## Tutorials

1. Install this package and vosk

  ```bash
  sudo apt install ros-${ROS_DISTRO}-ros-vosk
  ```
  don't forget to run `catkin_make`
  
2. Install Dependencies

  If using ROS MELODIC run first: 
  ```bash
  sudo apt install python3-pip 
  ```
  Then run for MELODIC & NOETIC:
  ```bash
  roscd ros_vosk
  pip3 install -r requirements.txt
  ``` 
  And if you want to use the TTS engine please run:
  ```bash
  sudo apt install espeak
  pip3 install pyttsx3
  ```  

## Launch
  Launch the speech recognition node
  ```bash
  roslaunch ros_vosk ros_vosk.launch
  ```
  or by running:
  ```bash
  rosrun ros_vosk vosk_node.py
  ```
### Parameters
| Param | Description | Values | Default 
| --- | --- | --- | ---
| ___models_path___ | path to a folder where vosk audio models are stored | string | -
| ___use_tts_engine___ | use tts | True/False | False

## Interface

### Node vosk_engine
___Published topics___
| Topic | Type | Description 
| --- | --- | --- 
___vosk/speech_recognition/vosk_result___ | ros_vosk/speech_recognition | a custom "speech_recognition" message
___vosk/speech_recognition/final_result___ | [std_msgs/String](http://docs.ros.org/en/api/std_msgs/html/msg/String.html) | a string with the final result
___vosk/speech_recognition/partial_result___ | [std_msgs/String](http://docs.ros.org/en/api/std_msgs/html/msg/String.html) | a string with the partial result

___Subscribed topics___
| Topic | Type | Description 
| --- | --- | --- 
___vosk/tts/status___ | [std_msgs/Bool](http://docs.ros.org/en/api/std_msgs/html/msg/Bool.html) | the state of the tts engine. True if it is speaking False if it is not. If the status is true vosk_node won't process the audio stream so it won't listen to itself 

### Node tts_engine
___Published topics___
| Topic | Type | Description 
| --- | --- | --- 
___vosk/tts/status___ | [std_msgs/Bool](http://docs.ros.org/en/api/std_msgs/html/msg/Bool.html) | the state of the engine. True if it is speaking False if it is not.

___Subscribed topics___
| Topic | Type | Description 
| --- | --- | --- 
___vosk/tts/phrase___ | [std_msgs/String](http://docs.ros.org/en/api/std_msgs/html/msg/String.html) | get a string to say 

## Author
Angelo Antikatzidis <an.antikatzidis@gmail.com>
Nickolay V. Shmyrev <nshmyrev@gmail.com>
