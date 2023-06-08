# An Affordable, Real-Time, Web-Based, Open-Source and Open-Hardware Motion Capture System

## **Authors**

### Siva Nagi Reddy Munaganuru, MS-CS student at Arizona State University

### Pavan Krishna Reddy Madireddy , MS-CS student at Arizona State University

### Assegid Kidane, Engineer at Arizona State University

### Tejaswi Linge Gowda, Professor at Arizona State University


![architecture_1](https://github.com/Mesquite-Mocap/about.mesquite.cc/assets/110155812/91e38e99-c0b8-406f-a594-c420e26e78cf)


## **Abstract**

This paper introduces an affordable, flexible, and real-time motion capture(M0 Cap) system leveraging wearable IMU sensors.Unlike existing solutions, our system forgoes complex camera setups and expensive Inertial Measurement Units (IMU) based solutions . The essence of our solution lies in the data processing step, which incorporates a sensor fusion algorithm using the Attitude and Heading Reference System (AHRS), axis rotations, and translations based on the Biovision Hierarchy structure. The processed data accurately animates a 3D human skeleton model in real-time, effectively mimicking the movements of the wearer. Users can interact with and record these movements through an intuitive web interface, which provides a three-dimensional representation of human motion. While not specifically tailored for a single use case, our system offers significant potential for diverse applications, including gait analysis, sports training, animation, and more. This flexibility makes our system a valuable tool for researchers, clinicians, trainers, and animators alike.


![architecture_2](https://github.com/Mesquite-Mocap/about.mesquite.cc/assets/110155812/40c57f29-0b9d-4b1a-a02e-fce461a0b614)


## **Introduction**

Motion Capture (MoCap) technology, renowned for its capacity to record detailed human movements, has found widespread applications in fields such as biomechanical research, clinical rehabilitation, animation, and interactive entertainment. The recent surge in virtual and augmented reality applications has further fueled the demand for high-quality, accessible MoCap systems.

Traditionally, optical MoCap systems, characterized by multiple cameras tracking markers on a subject, have been the norm. Despite providing high-resolution, accurate data, they suffer from significant drawbacks including complex setup, high costs, and the need for optimal lighting conditions. In response to these challenges, there has been a shift towards the development and use of inertial measurement unit (IMU) based systems. IMU-based MoCap systems are portable, easy to use, and do not depend on external environmental conditions, making them ideal for use outside a studio setting. Various companies, such as Xsens, have introduced wearable IMU-based MoCap systems. However, these solutions are still costly, often due to proprietary hardware and software, and the use of high-end IMUs to ensure data quality.

To address these challenges, we present an affordable, real-time MoCap system using low-cost IMUs (MPU9250 or BNO08X) interfaced with a dual-core ESP32 microcontroller. Our system effectively processes raw sensor data to generate an accurate 3D model mirroring the user's movements. It features an interactive and user-friendly web interface, powered by Three.js graphics, which presents a virtual human skeleton that mimics the wearer's actions in real-time. This web-based approach offers a flexible platform, facilitating remote monitoring and expanding possibilities for at-home applications.

In addition, our system integrates a Biovision Hierarchy (BVH) recorder for capturing and replaying human motions. Our ongoing work focuses on enhancing the system's capabilities, including position tracking using a Recurrent Neural Network (RNN) model. Our efforts underscore our goal to make MoCap technology more accessible, versatile, and user-focused.

## **System Design**
Our proposed system is a mix of both hardware and software components working together seamlessly. It primarily comprises wearable sensors (MPU9250 or BNO08X) and a dual-core ESP32 microcontroller affixed to the user’s body. Furthermore, a Node.js server operates on a central computer, overseeing data acquisition, data processing, and 3D visualization through a suite of JavaScript-based components.

### **Hardware**

![MMcap](https://github.com/Mesquite-Mocap/about.mesquite.cc/assets/110155812/eb8d7779-2d1f-4f2f-9cd6-0a22c6a36aba)

The comprehensive system includes 15 wearable devices strapped to different parts of the user's body as illustrated in Fig above . Flexibility is key in our design; users can choose to use the devices on specific body parts such as the upper body, lower body, or legs. Each device consists of a self-calibrated IMU sensor (BNO08x with 9 DOF) and a dual-core ESP32 microcontroller. The microcontroller dedicates one core to reading quaternion data (to circumvent Euler's gimbal lock issue) from the connected IMU via the SCL and SDL pins. The other core broadcasts this data through web sockets at a rate of 30 frames per second, a value that can potentially be increased. The devices operate on battery power and are completely wireless, enhancing user mobility.

### **Software**

At the core of our software solution is a Node.js-based web server. To minimize computational overhead, the server employs a web worker that consistently reads data from the web sockets. Upon reception, each bone's data is processed separately. The raw sensor data, initially based on the local sensor's reference system, is converted to align with the reference system of the Three.js scene. We then adjust the rotation for each bone, accounting for its parent's rotation per the Biovision Hierarchy structure, and its initial T-pose value. When users stand in the T-pose and click the 'T-pose' button on the website, we record the rotation of each bone, which is then used as an offset for all future data. Consequently, we can animate the 3D human skeleton.

Furthermore, our system includes a Biovision Hierarchy (BVH) recorder. When the user initiates the record button on the website, the system traverses the Three.js skeleton, records the Euler rotation of each joint in the global frame, and saves this data in a BVH file. This feature allows for convenient recording and subsequent playback of motion.

## **Key Features**

### *Affordable Hardware:* 

Our system uses low-cost, easily accessible hardware components such as MPU9250, BNO08X, and a dual-core ESP32.

### *Real-Time Visualization:* 

The Node.js server processes the IMU data using the Mahony AHRS algorithm to derive rotations, which are then mapped onto a 3D human skeleton visualized in a Three.js scene.

### *High Capture Rate:*

Our system can achieve up to 45 frames per second, providing smooth motion tracking.

### *Future Enhancement Plans:*

We aim to further enhance the frame rate and incorporate Bluetooth as a data transfer protocol. We also plan to develop a Recurrent Neural Network (RNN) for real-time positional tracking.

### *Biovision Hierarchy (BVH) Recorder:*

The system includes a BVH recorder, enabling users to record, store, and replay the captured movements.

## **Statement of Need:**

The need for efficient and cost-effective motion capture solutions has never been greater, with increasing demand in industries like film, animation, healthcare, and fitness. Traditional solutions either require costly, space-bound equipment, or they lack real-time capture capabilities. Our innovative approach fills this gap by providing an affordable, flexible, and nearly real-time solution to motion capture. This technology is designed to serve animation creators, filmmakers, health diagnostics professionals, fitness coaches, and any others who could benefit from precise motion capture. As we continue to enhance its capabilities, we anticipate even broader applications and accessibility for this technology.

## **Installation Instructions:**

### **Prerequisites**
Ensure you have Node.js installed on your machine. If you don't have Node.js installed, you can download it from the [Official Website](https://nodejs.org/en/download)

### **Step 1: Clone the Repository**
Clone the repository to your local machine. This can be done using the following command: **git clone https://github.com/Mesquite-Mocap/mesquite.cc-app**

### **Step 2: Run the Node.js Server**
Navigate to the repository folder that you've just cloned. Once you are in the right directory, you can start the server by running the following command:  **node server.js**

This will start the server on port **3000** and initiate two WebSocket servers. The first WebSocket server is at the route **/hub**, which receives data from the IMUs. This server then relays the messages to the second WebSocket server at the route **/web_client**.

### **Step 3: Connect the IMUs**
Once the server is running, you can start transmitting data from your IMUs to the **/hub** route of the WebSocket server.

### **Step 4: View the 3D Scene**
The static files with the Three.js scene listen to the /web_client route. As the server receives a message, it processes it, converts it into quaternion, and does the axis rotation. Then, it checks if the particular bone has any dependencies, offsets the dependency, and then maps it to the Three.js human skeleton.

You can view the 3D scene by opening **http://localhost:3000**.

![threejs_scene](https://github.com/Mesquite-Mocap/about.mesquite.cc/assets/110155812/c6ca0868-d1b3-4e72-8214-ffc32a959fc1)

## **Acknowledgements:**

We would like to express our sincere gratitude to **Bhargav Ragunath** for his instrumental help with hardware guidence and testing throughout the project. His expertise and dedication were invaluable.

Our heartfelt thanks go to the **School of Arts, Media and Engineering at Arizona State University**. The availability of the school's labs, resources, and continuous support contributed significantly to the successful completion of our research.

## **References**

### [A Fully Wireless Wearable Motion Tracking System with 3D Human Model for Gait Analysis by Kevin Lee and Wei Tang](https://www.mdpi.com/1424-8220/21/12/4051)

### [GAIT ANALYSIS USING IMU SENSOR by Trupti Gujarathi and Kalyani Bhole](https://ieeexplore.ieee.org/abstract/document/8944545)

