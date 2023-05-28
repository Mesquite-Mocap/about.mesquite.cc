# An open-source, open-hardware, web-based Mocap system

## **Abstract**

As motion capture (Mo-Cap) technology finds its place in industries such as film, gaming, healthcare, and fitness, the need for cost-effective and real-time solutions has grown. Current systems either require camera setups that limit mobility and are sensitive to lighting conditions, or IMU-based solutions that are expensive and incapable of real-time data capture. To address this, we present an affordable, flexible, and nearly real-time Mo-Cap system. Our solution utilizes low-cost hardware components like MPU9250, BNO08X, and a dual-core ESP32. The system captures data from these IMUs, worn on the body, and transmits this data to a local server via web sockets. A Node.js server processes the data using the Mahony AHRS algorithm, translating the raw IMU data into corresponding human skeleton movements. These movements are then visualized in real-time in a Three.js scene, providing users a comprehensive and interactive view of the motion capture data.

## **Introduction**

Imagine an animated film where the characters move in a way that feels natural and lifelike. Behind the scenes, this often involves a technology called motion capture, which records real people's movements and then uses this data to animate the characters. Now, imagine this technology being available to not just animators or game developers, but also doctors for diagnosing movement-related health issues, or fitness professionals to improve exercise techniques, all in an affordable and flexible setup. This is where our new motion capture system comes into play. It uses devices called Inertial Measurement Units (IMUs) that are worn on the body, capturing every motion and transforming it into a real-time digital model of your body in motion. This less expensive, more flexible, and near real-time system could revolutionize the way we use motion capture.

## **Key Features**

### *Affordable Hardware:* 

Our system uses low-cost, easily accessible hardware components such as MPU9250, BNO08X, and a dual-core ESP32.

### *Real-Time Visualization:* 

The Node.js server processes the IMU data using the Mahony AHRS algorithm to derive rotations, which are then mapped onto a 3D human skeleton visualized in a Three.js scene.

### *High Capture Rate:*

Our system can achieve up to 30 frames per second, providing smooth motion tracking.

### *Future Enhancement Plans:*

We aim to further enhance the frame rate and incorporate Bluetooth as a data transfer protocol. We also plan to develop a Recurrent Neural Network (RNN) for real-time positional tracking.

### *Biovision Hierarchy (BVH) Recorder:*

The system includes a BVH recorder, enabling users to record, store, and replay the captured movements.

## **Statement of Need:**

The need for efficient and cost-effective motion capture solutions has never been greater, with increasing demand in industries like film, animation, healthcare, and fitness. Traditional solutions either require costly, space-bound equipment, or they lack real-time capture capabilities. Our innovative approach fills this gap by providing an affordable, flexible, and nearly real-time solution to motion capture. This technology is designed to serve animation creators, filmmakers, health diagnostics professionals, fitness coaches, and any others who could benefit from precise motion capture. As we continue to enhance its capabilities, we anticipate even broader applications and accessibility for this technology.

