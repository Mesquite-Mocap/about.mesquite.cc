---
title: 'Mesquite Mocap: An Affordable, Real-Time, Web-Based, Open-Source and Open-Hardware Motion Capture System'
tags:
  - Computer Science
  - Motion Capture
  - Mocap Technology
  - Inertial Measurement Unit
authors:
  - name: Poojan Vanani
    orcid: 0009-0007-0930-6400
    equal-contrib: true
  - name: Romir Patel
    orcid: 0009-0002-1642-9525
    equal-contrib: true
  - name: Darsh Patel
    orcid: 0009-0006-4559-4027
    equal-contrib: true
  - name: Tejaswi Gowda Ph.D.
    orcid: 0000-0002-0896-6526
    corresponding: true
    equal-contrib: true
date: 
---


## **Introduction**
 




## **Background Motivation**


## **System Architecture**

The proposed system consists of 15 wearable pods which are attached to the different bones of the human  body. The pods are tied on straps with the help of powerful magnets for ease. Each pod is  marked with the name of the human bone it monitors. The system is completed with an Android mobile phone  that uses visual odometry to determine the position of the human body in 3D space. Every  pod has a 9-axis IMU sensor (T ICM by LilyGO) and an  ESP32 dual-core microcontroller.

The system architecture of this ESP32-based motion tracking system is designed for real-time wireless transmission of IMU data using ESP-NOW communication. The ESP32 microcontroller operates on a dual-task FreeRTOS architecture, where one core is dedicated to reading quaternion data from the IMU via the I2C interface (SCL and SDA pins), while the other core transmits this data wirelessly at a rate of 32 frames per second (FPS). The quaternion data, representing the 3D orientation of each pod, is processed to prevent Euler’s gimbal lock issue.

To this end, the system uses ESP-NOW, a low latency wireless protocol, for wireless  transmission of motion information in the form of quaternions (x, y, z, w),  battery voltage and a separate identifier for every body part being tracked. In the event of data packet  loss, the system is designed to transition to deep sleep mode in order to preserve battery life. Furthermore,  the ESP32 has a in-built battery monitoring system that uses the ADC module to sample the battery voltage  and make changes to the system operation based on the voltage. The system also has a physical button that  enables the user to put the system into deep sleep mode directly when needed. The success or failure of  data transmission is also indicated by an LED, which blinks its states accordingly.

To ensure error handling and system reliability the ESP32 persists to check the validity of the received  data. In the event of all quaternion values being zero, presumed a sensor failure, the system will reboot  itself. The IMU setup is done by first enabling Digital Motion Processor (DMP) features to  extract high precision orientation data from raw gyroscope and accelerometer readings. This data is then collected and sent  to a central processing device where it is used for real time motion tracking in applications like robotics, virtual  reality (VR), and biomechanical analysis. This architecture is meant to guarantee that the system is  robust, low power and efficient and thus suitable for continuous tracking tasks.        The ESP32 is designed  to handle failures and ensure system reliability by always validating the data received. In the case of all quaternion  values being zero, it is possible that a sensor has failed, and in this case the system will  reboot. The IMU setup process involves first, enabling Digital Motion Processor (DMP) features to  enable the extraction of high precision orientation data from gyroscope and accelerometer raw readings. The collected motion data  is then sent to a central processing device for real time motion tracking in areas such as robotics, virtual  reality (VR) and biomechanical analysis. This architecture ensures that the system is robust, low  power and efficient and thus suitable for continuous tracking tasks.

Right after data acquisition, the quaternion form of the motion data is sent to a web based interface  through WebSockets, and is further processed to update a 3D skeletal model in real  time. After receiving this data, each body part's transformation is saved in the mac2Bones object  that holds the information about the global, local and calibration states for the accurate motion tracking. The system  bootstraps by setting some quaternions for different bones like spine, hips, arms,  legs, and hands to map correctly to the 3D skeletal model.

To improve the accuracy of motion tracking, Kalman filtering is used to reduce noise especially in the  position estimation. Quaternion transformations like axis swapping and normalization are used to make sure that sensor data is properly  aligned between different devices. The system uses spherical linear interpolation (slerp) of bone orientations to  update them in real time, for seamless transition between movement states. Moreover, real time position tracking of  the hips is also implemented, which updates a trail of position to show movement over a time  period.

The calibration is done manually or automatically at the initial sensor values are sensor values. Sensor selection,  calibration triggers, and real-time tracking status are means through which users can interact with the system and make  it adaptable and flexible. The architecture also incorporates real-time feedback of the sensors' performance from battery level  monitoring and connection status updates. The combination of quaternion-based transformations, hierarchical bone mapping, and Kalman  filtering produces a very precise and timely response motion capture system, and thus it is suitable for their application  in biomechanics, virtual reality, and robotics.




## **Mapping the Human Motion**



## **Key Features**
 

## **Statement of Need:**

