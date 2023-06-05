# An Affordable, Real-Time, Web-Based, Open-Source and Open-Hardware Motion Capture System

## **Authors**

### Siva Nagi Reddy Munaganuru, MS-CS student at Arizona State University

### Pavan Krishna Reddy Madireddy , MS-CS student at Arizona State University

### Tejaswi Linge Gowda, Professor at Arizona State University

## **Abstract**

As motion capture (Mo-Cap) technology finds its place in industries such as film, gaming, healthcare, and fitness, the need for cost-effective and real-time solutions has grown. Current systems either require camera setups that limit mobility and are sensitive to lighting conditions, or use **Inertial Measurement Unit** (IMU) based solutions offer more flexibility, however, existing implementations are often expensive or unable to capture in real-time due to the complexity of machine learning models employed. To address this, we present an affordable, flexible, and nearly real-time Mo-Cap system. Our solution utilizes low-cost hardware components like MPU9250, BNO08X, and a dual-core ESP32. The system captures data from these IMUs, worn on the body, and transmits this data to a local server via web sockets. A Node.js server processes the data using the Mahony AHRS algorithm, translating the raw IMU data into corresponding human skeleton movements. These movements are then visualized in real-time in a Three.js scene, providing users an interactive view of the motion capture data.

## **Introduction**

Our Mo-Cap system ingeniously integrates readily available hardware with sophisticated software. It leverages Inertial Measurement Units (IMUs) – specifically, the MPU9250 or BNO08X sensors – strapped onto the user's body to chronicle their movements. These IMUs are connected to a dual-core ESP32 microcontroller, a crucial component due to its dual-core capabilities, where one core is dedicated to reading sensor data, and the other for transmitting it wirelessly.

Data transmission happens in **real-time** using web sockets at 45 frames per second, a protocol that enables continuous two-way communication between the client and the server. The server, built with Node.js, is responsible for receiving this data and processing it using the Mahony AHRS algorithm. This algorithm is crucial for converting raw IMU data into quaternion values, which represent the orientation of each IMU (and therefore each body part) in 3D space.

The processed data is then mapped to a 3D human skeleton model, built using Blender, a notable 3D graphics tool. Our human skeleton model has been designed with biomechanical constraints, emulating the intricate range of human joint movement. This approach effectively addresses the limitations of conventional motion capture systems that require both 3D orientation and position for each joint. Instead, by focusing solely on 3D orientation data, and using it to adjust the Human skeleton model, we have achieved improved accuracy in motion representation. And when assigning bone orientation to the skeleton, the system recognizes if a bone has a parent according to the BVH structure, and subsequently offsets the parent's rotations. As users move, the model matches these movements in near real-time, offering a dynamic and intuitive visualization of the captured motion data.

Moreover, our system integrates a Biovision Hierarchy (BVH) recorder, allowing users to record, store, and replay captured movements - a feature that proves invaluable for ongoing review and analysis. The enhanced ability of our system to mirror and record human movement, combined with its improved accuracy, opens up a plethora of potential applications ranging from animation and filmmaking to health diagnostics and fitness training."

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

## **Installation Instructions:**

## **Acknowledgements:**

## **References**

