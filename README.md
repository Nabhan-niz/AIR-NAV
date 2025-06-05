# AIR-NAV
# Hand Gesture Control using OpenCV & MediaPipe

## Overview
This project implements a **gesture-based control system** using OpenCV and MediaPipe. It enables users to:
- Control the **mouse cursor** with hand movements.
- Perform **left-click, right-click, and dragging** gestures.
- Adjust **system volume** using a "Shaka" gesture.
- Navigate **PowerPoint slides** through hand motions.
- 
## Sample Outputs

## Features
✅ **Smooth & Precise Mouse Control**  
✅ **PowerPoint Navigation** (Next & Previous slides)  
✅ **Volume Adjustment with Hand Gestures**  
✅ **Optimized Performance with Async Video Capture**  

## Requirements
Ensure you have the following dependencies installed:
```bash
pip install opencv-python mediapipe numpy pyautogui pycaw comtypes
Got it! Here's the complete **README.md** file, formatted properly so you can **copy-paste** it directly into your project. 🚀  

```markdown
# Hand Gesture Control using OpenCV & MediaPipe

## Overview
This project implements a **gesture-based control system** using OpenCV and MediaPipe. It enables users to:
- Control the **mouse cursor** with hand movements.
- Perform **left-click, right-click, and dragging** gestures.
- Adjust **system volume** using a "Shaka" gesture.
- Navigate **PowerPoint slides** through hand motions.

## Features
✅ **Smooth & Precise Mouse Control**  
✅ **PowerPoint Navigation** (Next & Previous slides)  
✅ **Volume Adjustment with Hand Gestures**  
✅ **Optimized Performance with Async Video Capture**
```

## Installation
### **Install Required Dependencies**
```bash
pip install opencv-python mediapipe numpy pyautogui pycaw comtypes
```

### **Clone the Repository**
```bash
git clone <your-repository-link>
```

## How to Run
### **Navigate to the Project Folder**
```bash
cd HandGestureControl
```

### **Run the Script**
```bash
python gesture_control.py
```

## Usage Instructions
- Move your **index finger** to control the cursor.
- **Pinch thumb & index finger** to perform a left-click.
- **Touch index & middle fingers together** for a right-click.
- **Thumbs-up gesture** enables dragging mode.
- **Shaka gesture 🤙** toggles volume control.
- **Swipe gestures** navigate PowerPoint slides.

## Code Structure
### **Python Code - Gesture Control Script**
```python
import cv2
import mediapipe as mp
import pyautogui
import numpy as np
import math
import time
import threading
from pycaw.pycaw import AudioUtilities, IAudioEndpointVolume
from comtypes import CLSCTX_ALL, cast, POINTER
import win32gui  

# ✅ Faster Video Capture
class VideoCaptureAsync:
    def __init__(self, src=0):
        self.cap = cv2.VideoCapture(src, cv2.CAP_DSHOW)
        self.cap.set(cv2.CAP_PROP_FRAME_WIDTH, 640)
        self.cap.set(cv2.CAP_PROP_FRAME_HEIGHT, 480)
        self.running = True
        self.frame = None
        self.thread = threading.Thread(target=self._update, args=())

    def start(self):
        self.thread.start()
        return self

    def _update(self):
        while self.running:
            ret, frame = self.cap.read()
            if ret:
                self.frame = cv2.flip(frame, 1)

    def read(self):
        return self.frame

    def stop(self):
        self.running = False
        self.thread.join()
        self.cap.release()

# ✅ Other parts of the script...
```



## Future Improvements
🔹 Enhance gesture recognition for multi-hand support  
🔹 Add custom calibration settings  
🔹 Improve click precision and responsiveness  



