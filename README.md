# An open-source, open-hardware, web-based Mocap system

## **Abstract**

As motion capture (Mo-Cap) technology finds its place in industries such as film, gaming, healthcare, and fitness, the need for cost-effective and real-time solutions has grown. Current systems either require camera setups that limit mobility and are sensitive to lighting conditions, and **Inertial Measurement Unit** (IMU) based solutions offer more flexibility, however, existing implementations are often expensive or unable to capture in real-time due to the complexity of machine learning models employed. To address this, we present an affordable, flexible, and nearly real-time Mo-Cap system. Our solution utilizes low-cost hardware components like MPU9250, BNO08X, and a dual-core ESP32. The system captures data from these IMUs, worn on the body, and transmits this data to a local server via web sockets. A Node.js server processes the data using the Mahony AHRS algorithm, translating the raw IMU data into corresponding human skeleton movements. These movements are then visualized in real-time in a Three.js scene, providing users aN interactive view of the motion capture data.

## **Introduction**

Our  motion capture system is a synthesis of software and affordable, readily available hardware components. It utilizes Inertial Measurement Units (IMUs) – specifically, MPU9250 and BNO08X sensors – attached to the user's body to record their movements. These IMUs are connected to a dual-core ESP32 microcontroller, a crucial component due to its dual-core capabilities, where one core is dedicated to reading sensor data, and the other for transmitting it.

Data transmission happens in **real-time** using web sockets, a protocol that enables continuous two-way communication between the client and the server. The server, built with Node.js, is responsible for receiving this data and processing it using the Mahony AHRS algorithm. This algorithm is crucial for converting raw IMU data into quaternion values, which represent the orientation of each IMU (and therefore each body part) in 3D space.

The processed data is then mapped to a 3D human skeleton model visualized using Three.js, a popular library for creating 3D graphics in the browser. As the user moves, the skeleton mimics these movements in near real-time, providing an interactive and intuitive visualization of the captured motion data. Our system also includes a Biovision Hierarchy (BVH) recorder, which allows users to record, store, and replay the captured movements, an invaluable feature for review and analysis.

This holistic approach to motion capture brings a novel contribution to the field, combining low-cost hardware, real-time data processing, and dynamic 3D visualization, which can be of immense value to various industries from animation and filmmaking to healthcare and fitness.

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

