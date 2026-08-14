# AI-Driven Video Surveillance System with Anomaly Detection

An AI-based video surveillance system that monitors a camera feed for potential security incidents such as weapon detection and camera obstruction. The system uses YOLO for weapon detection and OpenCV-based image analysis for full and partial camera blockage detection.

## Features

- Real-time video surveillance using OpenCV
- YOLO-based weapon detection
- Full camera blockage detection
- Partial camera blockage detection
- Automatic incident snapshot capture
- Email alerts with incident snapshots
- SMS alerts using Twilio
- Event cooldown mechanism to reduce repeated alerts
- Timestamped event logging
- Multi-camera architecture using Python threading

## Technologies Used

- Python
- OpenCV
- YOLO / Ultralytics
- NumPy
- Python-dotenv
- SMTP
- Twilio
- Multithreading

## How It Works

The system captures frames from a connected camera and performs multiple security checks.

### 1. Weapon Detection

A custom-trained YOLO model is used to detect weapons in the camera feed.

When a weapon is detected:

1. The detected object is highlighted.
2. A snapshot is captured.
3. An email alert is triggered.
4. An SMS alert is triggered.
5. A cooldown period prevents repeated alerts from being sent continuously.

### 2. Full Camera Blockage Detection

The system calculates the average brightness of the camera frame.

If the brightness remains below a predefined threshold for a specified duration, the camera is considered fully blocked.

A snapshot is captured and alerts are triggered.

### 3. Partial Camera Blockage Detection

The system calculates the ratio of dark pixels in the frame.

If a sufficiently large portion of the frame remains dark for the configured detection period, the system identifies the camera as partially blocked.

### 4. Incident Snapshots

Snapshots are automatically organized according to the detected event:

```text
snapshots/
├── fully_blocked/
├── partially_blocked/
└── weapon/