# 🕊️ Bird Detection near Wind Turbines  
**(YOLOv8 + Streamlit Dashboard Project)**

---

## 📖 Overview

This project simulates a **bird collision prevention system** for wind turbines using **YOLOv8 object detection**.  

It can:
- Detect birds in real-time from **webcam** or **video**.
- Simulate **STOP/ RUN turbine control** when birds enter the rotor sweep zone.
- Provide a **visual dashboard** (Streamlit app) with alerts, logs, and charts.
- Generate **synthetic videos** with flying birds and a rotating turbine for demos.

⚡ This project is designed for **educational & demo purposes** when real turbine access is not available.

---

## ✨ Features

- **YOLOv8 real-time bird detection**
- **Interactive dashboard** with:
  - Live video feed + bounding boxes
  - Rotor sweep zone (blue box)
  - Status LED: 🟢 RUN / 🔴 STOP
  - Banner alerts for risk
  - Live line chart (birds & risk)
  - Recent event logs
- **Synthetic video generator** for demo birds + turbine
- **Event logging** to `outputs/logs/events.log`
- **Annotated frames & videos** saved to `outputs/detections/`

---

## 📂 Project Structure

```
bird_turbine_project/
│
├── data/
│   ├── videos/                # Test / synthetic videos
│   ├── images/                # Training images (optional)
│   └── bird_data.yaml         # Dataset config for YOLO training
│
├── models/                    # Store custom YOLO weights (optional)
│
├── outputs/
│   ├── logs/                  # Event logs
│   └── detections/            # Saved annotated frames / videos
│
├── src/
│   ├── app.py                 # Streamlit dashboard
│   ├── detect_birds.py        # CLI demo (non-dashboard)
│   ├── make_synthetic_video.py# Synthetic video generator
│   ├── train_model.py         # YOLO training wrapper
│   ├── utils.py               # Drawing + logging helpers
│   └── turbine_control.py     # Turbine STOP/ RUN simulation
│
├── requirements.txt           # Python dependencies
└── README.md                  # Project documentation
```

---

## 🔧 Setup

### 1. Navigate to project folder
```powershell
cd C:\Users\Kylean\Desktop\bird_turbine_project
```

### 2. Create and activate a virtual environment
```powershell
python -m venv venv
venv\Scripts\activate
```

### 3. Install dependencies
```powershell
pip install -r requirements.txt
pip install streamlit pandas
```

---

## ▶ Run the Dashboard

Start the app with:
```powershell
python -m streamlit run src/app.py
```

- The browser will open at **http://localhost:8501** or **http://localhost:8502**.
- Use the **sidebar (left)** to configure the system.

---

## 🎥 Video Sources

### 1. Webcam
- Choose **Webcam (0)** in the sidebar.
- Click **▶ Start**.
- If it fails:
  - Close apps using the camera (Zoom/Teams).
  - Allow camera access in **Windows Privacy Settings**.

### 2. Synthetic video
1. Generate a demo video:
   ```powershell
   python -m src.make_synthetic_video
   ```
   This creates:
   ```
   data/videos/birds_synth_better.mp4
   ```

2. In the sidebar, choose **Synthetic: birds_synth_better.mp4**.

3. Click **▶ Start** to run the demo.

---

## 🕹️ How the Dashboard Works

- **Blue box = Rotor sweep zone**  
  If birds enter this area → system triggers **STOP**.

- **Green LED = RUN**  
  Turbine simulated as running.

- **Red LED = STOP**  
  Bird risk detected → turbine simulated STOP.

- **Top banner alerts**  
  Examples:
  - “BIRD RISK — TURBINE STOP”
  - “2 BIRDS DETECTED”

- **Line chart**  
  Shows birds detected and risk state over time.

- **Event table**  
  Displays the 10 most recent detections with timestamps.

- **Sidebar controls** let you:
  - Adjust **confidence threshold**
  - Adjust **ROI sliders** (sweep zone box)
  - Change **cooldown time**
  - Set **risk smoothing**
  - Enable saving frames or recording full videos

---

## 📂 Outputs

- **Logs** → `outputs/logs/events.log`
- **Frames** → `outputs/detections/frame_*.jpg`
- **Recorded video** → `outputs/detections/annotated_demo.mp4` (if enabled)

---

## 🧪 Training (Optional)

To fine-tune YOLOv8 on your own bird dataset:

```powershell
python -m src.train_model --data data/bird_data.yaml --model yolov8s.pt --epochs 100
```

Trained weights will be saved in:
```
runs/detect/train*/weights/best.pt
```

---

## ✅ Quick Demo Checklist (2 Minutes)

1. Generate synthetic video:
   ```powershell
   python -m src.make_synthetic_video
   ```
2. Launch dashboard:
   ```powershell
   python -m streamlit run src/app.py
   ```
3. In sidebar:
   - Select **Synthetic: birds_synth_better.mp4**
   - Click **▶ Start**
4. Watch:
   - Birds fly across the turbine
   - System switches between **RUN/STOP**
   - Logs and charts update live

---

## 📌 Notes

- Default detection class = **bird** (from COCO).  
- YOLO weights (`yolov8s.pt`) auto-download on first run.  
- System simulates turbine STOP/ RUN — no real hardware control.  
- Works with **webcam** or **video files**.

---

## 📣 Future Improvements

- Add **trajectory prediction** (stop turbine only if a bird’s path intersects blades).
- Add **alarm sounds** or **radar sweep overlay** in the dashboard.
- Train on **custom datasets** for higher accuracy.
- Deploy to **Jetson Nano / Raspberry Pi** for real-world edge AI.
