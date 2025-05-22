# Hand Gesture Controlled Presentation using OpenCV

This project introduces an **interactive presentation system** that allows users to control slides and annotate content using simple **hand gestures**, without touching a keyboard or mouse. Built using **Python**, **OpenCV**, and **PyAutoGUI**, the system offers a modern, accessible, and intuitive alternative to traditional presentation tools.

---

## Features

* **Touchless Slide Navigation** – Move forward or backward in a presentation using finger gestures.
* **On-Screen Drawing** – Annotate slides live during a presentation.
* **Pointer Control** – Highlight points using a virtual laser-pointer effect.
* **Erasing Mechanism** – Remove annotations with a simple three-finger gesture.
* **Control Zone Boundary** – A green boundary area is used to limit slide-change and erase gestures, reducing false positives due to random hand movements.
* **Real-Time Feedback** – Immediate system response for a smooth, natural presentation experience.

---

## How It Works

The system is designed around a **modular vision pipeline**:

### 1. Face & Hand Detection

* Uses OpenCV and `cvzone.HandDetector` to detect the presenter's face and dominant hand in real-time.

### 2. Gesture Recognition

* The system detects the number and arrangement of raised fingers.
* Different patterns correspond to different actions (e.g., one finger = draw, three fingers = erase).

### 3. Control Zone Implementation

* A **green line** at the top of the screen acts as a safe zone for specific gestures (slide navigation, erasing).
* Pointer and drawing actions can occur anywhere on the screen.

### 4. Command Execution

* PyAutoGUI is used to simulate keyboard/mouse actions such as:

  * Slide transitions
  * Pointer movement
  * Drawing annotations
  * Erasing content

---

## Gesture Controls

| Gesture (Finger Pattern) | Function Description                             |
| ------------------------ | ------------------------------------------------ |
| `[1,0,0,0,0]`            | Move to **previous** slide (within control zone) |
| `[0,0,0,0,1]`            | Move to **next** slide (within control zone)     |
| `[0,1,1,0,0]`            | Show **pointer** (highlight presentation area)   |
| `[0,1,0,0,0]`            | **Draw** on slide using finger path              |
| `[0,1,1,1,0]`            | **Erase** latest drawing (within control zone)   |

> Only the pointer and drawing gestures are allowed across the entire screen. Others must be performed above the green control line.

---

## Technology Stack

* **Programming Language**: Python 3
* **Computer Vision**: OpenCV
* **Gesture Detection**: cvzone
* **Mouse/Keyboard Simulation**: PyAutoGUI
* **Array Processing**: NumPy

---

## Installation

1. **Clone the repository**

```bash
git clone https://github.com/your-username/hand-gesture-presentation.git
cd hand-gesture-presentation
```

2. **Install required libraries**

```bash
pip install opencv-python cvzone numpy pyautogui
```

3. **Add slides**
   Place the images of your slides into the `/presentation` folder. They will be loaded dynamically during runtime.

---

## Usage

1. Connect a webcam to your system.
2. Run the application:

```bash
python main.py
```

3. Use gestures to control slides:

   * Raise fingers according to the gesture chart.
   * Stay within the green zone for slide navigation and erasing.
   * Use the entire screen for pointer and drawing.

4. Press `q` to quit the program.

---
