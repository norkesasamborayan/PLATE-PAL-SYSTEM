# PLATE-PAL Development Roadmap and Current Progress

## Current Development Status

Before starting the actual system development, the required development environment was prepared and configured. The following software and libraries have already been successfully installed and tested:

### Installed Software and Libraries

✅ Python 3.11.9

✅ Node.js v25.2.1

✅ npm v11.6.2

✅ Git v2.54.0

✅ OpenCV 4.13.0

✅ Easyocr 1.7.2

✅ PyTorch 2.12.1

✅ Ultralytics YOLOv11 (v8.4.75)


---

## Recommended Development Approach

Based on the PLATE-PAL system architecture, development should not begin with the mobile application or web dashboard. The most critical component is the Artificial Intelligence detection module because all other system functionalities depend on its output.

### System Workflow

Camera 1 (Helmet Detection)

CCTV Camera → YOLOv11 Helmet Detection → Violation Detection

Camera 2 (Plate Recognition)

CCTV Camera → License Plate Capture → EasyOCR → LSTM Correction → Final Plate Number

Integrated System Workflow

CCTV → YOLOv11 Helmet Detection → OCR + LSTM Plate Recognition → Database → Dashboard → Mobile Notification

---

# Recommended Database Architecture

The study proposes the use of MySQL and Firebase, which is the most suitable architecture for the system.

## MySQL Database

Used for permanent storage of:

* Rider Information
* Vehicle Information
* Violation Records
* Camera Records
* Administrator Accounts
* Reports and Analytics

## Firebase

Used for real-time communication:

* Push Notifications
* Mobile Synchronization
* Live Updates
* Real-Time Alert Delivery

### Example Workflow

1. AI detects a rider without a helmet.
2. License plate number is extracted.
3. Violation record is stored in MySQL.
4. Backend sends notification request to Firebase.
5. Mobile application receives an instant alert.

This approach is more efficient than relying solely on MySQL for real-time communication.

---

# Development Team Assignment

## Member 1 – Web and Backend Developer

Responsibilities:

* Node.js / Express Backend
* MySQL Database Management
* Firebase Integration
* Web Dashboard Development
* API Development

## Member 2 – AI and Embedded Systems Developer

Responsibilities:

* YOLOv11 Helmet Detection
* EasyOCR Integration
* LSTM Plate Recognition
* Raspberry Pi Integration
* Camera Processing

---

# PHASE 1 – Development Environment Setup (Completed)

### Week 1

Completed Installations:

* Python 3.11.9
* Node.js
* npm
* Git
* OpenCV
* PyTorch
* Ultralytics YOLOv11
* EasyOCR


Project Folder Structure:

PLATE-PAL/

├── ai-models/

├── backend/

├── frontend/

├── mobile/

├── database/

├── raspberrypi/

└── datasets/

---

# PHASE 2 – AI Development (Priority Phase)

### Week 2–3

Dataset Requirements

Helmet Detection Dataset

* 1,500+ Helmet Images
* 1,500+ No Helmet Images

Total:

* 3,000+ Images

Classes:

* helmet
* no_helmet

Training Platform

Recommended:

* Google Colab (Free GPU)

Alternative:

* Local Laptop Training (CPU Only)

Output:

best.pt

Expected Result:

✔ Detect Helmet

✔ Detect No Helmet

---

# PHASE 3 – License Plate Recognition

### Week 4

Camera 2 Workflow

Capture Image

↓

Detect Plate

↓

Crop Plate

↓

EasyOCR

↓

LSTM Correction

↓

Final Plate Number

Example:

EasyOCR Output:

ABC12B4

LSTM Correction:

ABC1234

Final Output:

ABC1234

---

# PHASE 4 – Database Design

### Week 5

Create MySQL Database Tables

* admins
* riders
* vehicles
* violations
* notifications
* cameras

Design database according to the approved ERD.

---

# PHASE 5 – Backend API Development

### Week 6

Build Express API

Endpoints:

POST /violation

GET /violations

POST /register-rider

POST /login

GET /dashboard

Workflow:

No Helmet Detected

↓

Plate Recognized

↓

Store Record in MySQL

---

# PHASE 6 – Firebase Integration

### Week 7

Configure:

* Firebase Authentication
* Firebase Cloud Messaging

Notification Example:

PLATE-PAL ALERT

Plate Number: ABC1234

Violation: No Helmet

---

# PHASE 7 – Dashboard Development

### Week 8

Dashboard Features

* Live Camera Feed
* Helmet Detection Monitoring
* Plate Recognition Monitoring
* Total Violations
* Analytics

Violation Records Module

* Plate Number
* Snapshot Evidence
* Date
* Time

---

# PHASE 8 – Mobile Application Development

### Week 9

Recommended Framework

Flutter + Firebase

Modules:

* Login
* Rider Registration
* Violation History
* Notifications
* Profile Management

---

# PHASE 9 – Raspberry Pi Integration

### Week 10

Camera 1

↓

Helmet Detection

Camera 2

↓

Plate Recognition

Integrate both outputs into the backend system.

---

# PHASE 10 – System Testing and Evaluation

### Week 11–12

Testing Conditions

* Morning
* Afternoon
* Night
* Different Distances
* Different Traffic Density

Evaluation Metrics

* Accuracy
* Precision
* Recall
* F1 Score

---

# Priority Development Order

1. Install EasyOCR
2. Install MySQL
3. Create Project Folder Structure
4. Collect Helmet Dataset
5. Train YOLOv11 Helmet Detection Model
6. Build Plate Recognition Module
7. Design MySQL Database
8. Develop Backend API
9. Configure Firebase
10. Develop Dashboard
11. Develop Mobile Application
12. Raspberry Pi Integration
13. Final Testing and Evaluation

---

## Current Progress Summary

Completed: Environment Setup (80%)

Installed:

* Python 3.11.9
* Node.js
* npm
* Git
* OpenCV
* PyTorch
* Ultralytics YOLOv11

Remaining:

* EasyOCR Installation
* MySQL Installation
* Dataset Collection
* Model Training

Next Immediate Task:

Install EasyOCR and begin collecting helmet/no-helmet datasets for YOLOv11 training.
