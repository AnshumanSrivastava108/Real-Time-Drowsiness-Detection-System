# Real-Time-Drowsiness-Detection-System

Drowsiness detection is a safety technology that can prevent accidents that are caused by drivers who fell asleep while driving. The objective of this project is to build a drowsiness detection system that will detect drowsiness through the implementation of computer vision system that automatically detects drowsiness in real-time from a live video stream and then alert the user with an alarm notification.

## Motivation 
According to the National Highway Traffic Safety Administration, every year about 100,000 police-reported crashes involve drowsy driving. These crashes result in more than 1,550 fatalities and 71,000 injuries. The real number may be much higher, however, as it is difficult to determine whether a driver was drowsy at the time of a crash. So, we tried to build a system, that detects whether a person is drowsy and alert him.

## Built With

* [OpenCV Library](https://opencv.org/) - Most used computer vision library. Highly efficient. Facilitates real-time image processing.
* [imutils library](https://github.com/jrosebr1/imutils) -  A collection of helper functions and utilities to make working with OpenCV easier.
* [Dlib library](http://dlib.net/) - Implementations of state-of-the-art CV and ML algorithms (including face recognition).
* [scikit-learn library](https://scikit-learn.org/stable/) - Machine learning in Python. Simple. Efficient. Beautiful, easy to use API.
* [Numpy](http://www.numpy.org/) - NumPy is the fundamental package for scientific computing with Python. 


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

1. Install and set up Python 3.
1. Install [cmake](https://github.com/Kitware/CMake/releases/download/v3.13.3/cmake-3.13.3-win64-x64.zip) in your system

## Running the application

1. Clone the repository. 

    ```
    git clone https://github.com/AnshumanSrivastava108/Real-Time-Drowsiness-Detection-System
    ```
    
1. Move into the project directory. 

    ```
    cd Real-Time-Drowsiness-Detection-System
    ```
 
1. (Optional) Running it in a virtual environment. 

   1. Downloading and installing _virtualenv_. 
   ```
   pip install virtualenv
   ```
   
   2. Create the virtual environment in Python 3.
   
   ```
    virtualenv -p C:\Python37\python.exe test_env
   ```    
   
   3. Activate the test environment.     
   
        1. For Windows:
        ```
        test_env\Scripts\Activate
        ```        
        
        2. For Unix:
        ```
        source test_env/bin/activate
        ```    

1. Install all the required libraries, by installing the requirements.txt file.

    ```
    pip install -r requirements.txt
    ```
    
1. Installing the dlib library.
     
    1. If you are using a Unix machine, and are facing some issues while trying to install the dlib library, follow [this guide](https://gist.github.com/ageitgey/629d75c1baac34dfa5ca2a1928a7aeaf).  
    
    1. If you are using a Windows machine, install cmake and restart your terminal. 
    
1. Run the application.

    ```
    python Real-Time-Drowsiness-Detection-System.py --shape-predictor shape_predictor_68_face_landmarks.dat --alarm Alert.wav
    ```

## Alogorithm

1. Capture the image of the driver from the camera.
2. Send the captured image to haarcascade file for face detection.
3. If the face is detected then crop the image consisting of the face only. If the driver is distracted then a face might not be detected, so play the buzzer.
4. Send the face image to haarcascade file for eye detection.
5. If the eyes are detected then crop only the eyes and extract the left and right eye from that image. If both eyes are not found, then the driver is looking sideways, so sound the buzzer.
6. The cropped eye images are sent to the hough transformations for detecting pupils, which will determine whether they are open or closed.
7. If they are found to be closed for five continuous frames, then the driver should be alerted by playing the buzzer.

For a more detailed explanation of this project check [*Real_Time_Drowsiness_Detection_System.pdf*](https://github.com/AnshumanSrivastava108/Real-Time-Drowsiness-Detection-System/blob/main/Real_Time_Drowsiness_Detection_System.pdf).

## Testing and Results in real-world scenario:

The tests were conducted in various conditions including:  

1.  Different lighting conditions.
2.  Drivers posture and position of the automobile drivers face. 
3.  Drivers with spectacles.  

Test case 1: When there is ambient light  

<p align="center">
<img width="600" height="350" src="Images/1.png ">
</p>
                                
Result: As shown above, when there is ambient amount of light, the automobile driver's face and eyes are successfully detected.  

Test case 2: Position of the automobile drivers face  

1. Centre Positioned

<p align="center">
<img width="600" height="350" src="Images/1.png ">
</p>
                                                               
RESULT: As shown in above, When the automobile driver's face is positioned at the Centre, the face, eyes, eye blinks, and drowsiness was successfully detected.  

2. Right Positioned

<p align="center">
<img width="600" height="350" src="Images/1.png ">
</p>
                              
RESULT: As shown in above, When the automobile driver's face is positioned at the Right, the face, eyes, eye blinks, and drowsiness was successfully detected. 

3. Left Positioned     
                             
<p align="center">
<img width="600" height="350" src="Images/1.png ">
</p>

RESULT: As shown in screen snapshot in above, when the automobile driver's face is positioned at the Left, the face, eyes, eye blinks, and drowsiness was successfully detected.  
Test case 3: When the automobile driver is wearing spectacles      
                                   
<p align="center">
<img width="600" height="350" src="Images/1.png ">
</p>

RESULT: As shown in  screen  snapshot  in  above, When  the  automobile  driver  is  wearing spectacles, the face, eyes, eye blinks, and drowsiness was successfully detected. 

Test case 4: When the automobile driver’s head s tilted    

<p align="center">
<img width="600" height="350" src="Images/1.png ">
</p>
                                          
RESULT: As shown in screen snapshot in above, when the automobile driver's face is tilted for more than 30 degrees from vertical plane, it was observed that the detection of face and eyes failed.  

The system was extensively tested even in real world scenarios, this was achieved by placing the camera on the visor of the car, focusing on the automobile driver. It was found that the system gave positive output unless there was any direct light falling on the camera.       




