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

<!-- Our Mo-Cap system ingeniously integrates readily available hardware with with a sophisticated yet straightforward software approach. It leverages Inertial Measurement Units (IMUs) – specifically, the MPU9250 or BNO08X sensors – strapped onto the user's body to chronicle their movements. These IMUs are connected to a dual-core ESP32 microcontroller,which dedicates one core to reading sensor data and peroform sensor fusion, and the other for wirelessly transmitting the data. 

Data transmission happens in **real-time** using web sockets at 45 frames per second, a protocol that enables continuous two-way communication between the client and the server. The server, built with Node.js, is responsible for receiving this data and processing it using the Mahony AHRS algorithm. This algorithm is crucial for converting raw IMU data into quaternion values, which represent the orientation of each IMU (and therefore each body part) in 3D space.

The processed data is then mapped to a 3D human skeleton model, built using Blender, a notable 3D graphics tool. Our human skeleton model has been designed with biomechanical constraints, emulating the intricate range of human joint movement. This approach effectively addresses the limitations of conventional motion capture systems that require both 3D orientation and position for each joint. Instead, by focusing solely on 3D orientation data, and using it to adjust the Human skeleton model, we have achieved improved accuracy in motion representation. And when assigning bone orientation to the skeleton, the system recognizes if a bone has a parent according to the BVH structure, and subsequently offsets the parent's rotations. As users move, the model matches these movements in near real-time, offering a dynamic and intuitive visualization of the captured motion data.

Moreover, our system integrates a Biovision Hierarchy (BVH) recorder, allowing users to record, store, and replay captured movements - a feature that proves invaluable for ongoing review and analysis. The enhanced ability of our system to mirror and record human movement, combined with its improved accuracy, opens up a plethora of potential applications ranging from animation and filmmaking to health diagnostics and fitness training."

This holistic approach to motion capture brings a novel contribution to the field, combining low-cost hardware, real-time data processing, and dynamic 3D visualization, which can be of immense value to various industries from animation and filmmaking to healthcare and fitness. -->

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

