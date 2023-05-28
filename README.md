# An open-source, open-hardware, web-based Mocap system

**Abstract**

In recent years, motion capture (Mo-Cap) technology has found wide-ranging applications, from animated movies and game development to healthcare diagnostics and fitness coaching. However, the traditional camera-based and IMU-based Mo-Cap solutions pose limitations due to space restrictions, sensitivity to lighting conditions, high costs, and the inability to capture in real-time. To address these challenges, we present an innovative, affordable, and nearly real-time IMU-based Mo-Cap solution. Our approach employs low-cost hardware and robust software that processes data from multiple IMUs worn on the body, representing the human skeleton's movements in real-time in a 3D visualization.

**Introduction**

Imagine an animated film where the characters move in a way that feels natural and lifelike. Behind the scenes, this often involves a technology called motion capture, which records real people's movements and then uses this data to animate the characters. Now, imagine this technology being available to not just animators or game developers, but also doctors for diagnosing movement-related health issues, or fitness professionals to improve exercise techniques, all in an affordable and flexible setup. This is where our new motion capture system comes into play. It uses devices called Inertial Measurement Units (IMUs) that are worn on the body, capturing every motion and transforming it into a real-time digital model of your body in motion. This less expensive, more flexible, and near real-time system could revolutionize the way we use motion capture.

**Key Features**

__Affordable Hardware: 

Our system uses low-cost, easily accessible hardware components such as MPU9250, BNO08X, and a dual-core ESP32.

__Real-Time Visualization: 

The Node.js server processes the IMU data using the Mahony AHRS algorithm to derive rotations, which are then mapped onto a 3D human skeleton visualized in a Three.js scene.

__High Capture Rate:

Our system can achieve up to 30 frames per second, providing smooth motion tracking.

__Future Enhancement Plans:

We aim to further enhance the frame rate and incorporate Bluetooth as a data transfer protocol. We also plan to develop a Recurrent Neural Network (RNN) for real-time positional tracking.

__Biovision Hierarchy (BVH) Recorder:

The system includes a BVH recorder, enabling users to record, store, and replay the captured movements.

**Statement of Need:**

The need for efficient and cost-effective motion capture solutions has never been greater, with increasing demand in industries like film, animation, healthcare, and fitness. Traditional solutions either require costly, space-bound equipment, or they lack real-time capture capabilities. Our innovative approach fills this gap by providing an affordable, flexible, and nearly real-time solution to motion capture. This technology is designed to serve animation creators, filmmakers, health diagnostics professionals, fitness coaches, and any others who could benefit from precise motion capture. As we continue to enhance its capabilities, we anticipate even broader applications and accessibility for this technology.

