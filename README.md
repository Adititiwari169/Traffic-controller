# 🚦 Intelligent Traffic Signal Simulation System

A smart traffic light controller that uses YOLO object detection to analyze vehicle density from intersection images and optimizes green light timings. This project simulates a **4-direction intersection** (North, East, South, West) and communicates the optimized signal durations to an **Arduino-controlled LED traffic light setup**.

---

## 🔍 Features

- Detects vehicle count using YOLOv4 object detection.
- Calculates green time dynamically based on traffic density.
- Simulates traffic light phases (Green, Yellow, Red).
- Communicates with Arduino to control LEDs in real-time.
- Simple Streamlit web interface for demonstration.

---

## 📁 Project Structure

```
intelligent-traffic-signal/
│
├── models/                     # YOLO model weights and config
│   ├── yolov4.weights
│   ├── yolov4.cfg
│
├── images/Intersection1/      # Input images for each direction
│   ├── North.jpg
│   ├── East.jpg
│   ├── South.jpg
│   └── West.jpg
│
├── vehicle_detection.py       # YOLO loading and vehicle detection logic
├── green_time_signal.py       # Green time calculation and Arduino communication
├── app.py                     # Streamlit app (main Python file)
├── arduino_code.ino           # Arduino sketch controlling the LED signals
├── coco.names                 # COCO class labels
└── README.md                  # You're here!
```

---

## 🛠 Requirements

### 🔗 Python Dependencies

- Python 3.8+
- OpenCV (`cv2`)
- NumPy
- PIL
- Streamlit
- PySerial

Install all dependencies using:

```bash
pip install -r requirements.txt
```

Example `requirements.txt`:

```txt
opencv-python
numpy
Pillow
streamlit
pyserial
```

### 🤖 Arduino Setup

- 1x Arduino Uno/Nano
- 3x LEDs (Red, Yellow, Green)
- 3x 220Ω resistors
- Breadboard + jumper wires
- Connect LEDs to **pins 2, 3, 4** (you can change this in `arduino_code.ino`)

---

## ⚙️ How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/intelligent-traffic-signal.git
cd intelligent-traffic-signal
```

### 2. Flash the Arduino Code

Upload `arduino_code.ino` using the Arduino IDE. Adjust the pin numbers if needed.

### 3. Run the Streamlit Web App

```bash
streamlit run app.py
```

This will open the web interface at `http://localhost:8501`.

### 4. Watch the Simulation

- Click "▶️ Run 4‑Direction Simulation"
- The system will:
  - Load each direction's image
  - Detect vehicles
  - Compute green time
  - Send timing (e.g., `N:37`) to Arduino
  - Simulate full light cycles

---

## ⚡ Serial Communication Protocol

- Format: `<Direction Letter>:<Time in Seconds>`
- Example: `N:25` → North direction gets 25s green
- Directions: `N`, `E`, `S`, `W`

---

## 🧪 Test Images

Place one `.jpg` image per direction inside:

```
images/Intersection1/
├── North.jpg
├── East.jpg
├── South.jpg
└── West.jpg
```

Use actual traffic images or simulated examples for testing.

---

## 🧠 Model Info

- YOLOv4 used for vehicle detection
- COCO dataset class IDs:
  - Relevant: `car`, `bus`, `truck`, `motorbike`, `bicycle`

---

## 🚨 Notes

- Ensure your COM port is set correctly in `app.py` (`ARDUINO_PORT = 'COM8'`)
- If only one LED is glowing, check:
  - Power/GND connections
  - Resistor values
  - Pin numbers in the Arduino sketch

---

## 📌 TODOs / Future Improvements

- Add camera feed support instead of static images
- Implement multi-intersection coordination
- Use real-time congestion prediction models
- Add GUI controls to override automatic timings

---

## 🤝 Contributing

1. Fork this repo
2. Create a feature branch: `git checkout -b feature-name`
3. Commit your changes
4. Push and open a PR 🚀

---


---

## 📜 License

MIT License. Feel free to use, modify, and distribute with credit.
