# Snapdragon-Hackathon

Adaptive Urban Guide: Sensory RL

An intelligent, real-time spatial awareness system designed specifically for the blind and visually impaired to assist in urban navigation. By combining Computer Vision, Q-Learning, and Multimodal Feedback, this application serves as a digital co-pilot for users navigating complex environments.

The Vision
In the unpredictable environment of modern cities, blind users require high-fidelity, real-time feedback to ensure safe movement. This project leverages on-device AI to distill environmental hazards into intuitive sensory cues:

Visual: AR Guide Way and High-Contrast HUD for users with low vision.

Auditory: Spatial Sonar with pitch-shifting based on proximity.

Haptic: Variable-intensity vibration alerts based on calculated risk to identify and avoid hazards.

Technical Architecture
1. Vision Engine (Edge AI)
The app utilizes TensorFlow.js with the coco-ssd model to perform on-device object detection. Running locally ensures:

Zero Latency: Critical for real-time safety and collision avoidance.

Privacy: No video data leaves the device.

Offline Capability: Functional in subways or areas with poor connectivity.

2. Kinematic Risk Assessment
The system treats objects as dynamic vectors rather than static images. It calculates Time-to-Collision (TTC) by monitoring the rate of change in an object's bounding box area (A):

Velocity Calculation: Velocity = Change in Area / Change in Time.

Risk Score: Risk = Area + (Velocity * Sensitivity).

3. RL Policy and Q-Learning Optimization
The RL Policy tab features an on-device simulation engine based on Q-Learning principles. This allows the system to tune its reaction sensitivity and safety buffers based on simulated environmental rewards and penalties.

State-Space Simulation: Evaluates 100+ episodes of approach velocities to find the optimal safety threshold.

Policy Tuning: The engine optimizes the mapping of detected states (distance/speed) to agent actions such as Stop, Warn, or Walk.

Adaptive Sensitivity: Higher sensitivity settings prioritize faster reaction times for high-velocity obstacles like cyclists or vehicles.

4. AR Guide Way
Using Bezier Curve logic, the app renders a Virtual Sidewalk on the camera feed. If an obstacle is detected on the left (negative deviation), the path dynamically curves to the right, providing a clear trajectory for the user to follow.

Features
Voice-Activated Search: Use Natural Language to find specific objects like chairs, bottles, or people using the Web Speech API.

Spatial Sonar: Square-wave audio oscillators change frequency as hazards approach, creating an auditory map of the surroundings.

High-Contrast Mode: Optimized for users with partial sight, featuring inverted styling and bold UI elements.

Policy Training: A dedicated trainer view to optimize the AI risk-tolerance level on the fly.

Installation and Setup
Clone the Repository: git clone [repository-url]

Deployment: Open index.html in a modern mobile browser. For full haptic and torch control, the project can be wrapped using Capacitor or Cordova to generate an Android APK.

Permissions: Ensure Camera and Microphone permissions are granted.

Background
This project applies mechanical engineering principles—specifically reinforcement learning and control theory—to mobile edge computing. It translates academic concepts into a lightweight, on-device Q-Learning policy optimized for mobile hardware to improve accessibility in urban environments.