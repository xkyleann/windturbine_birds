# 🎤 Demo Guide: Bird Detection near Wind Turbines
**(YOLOv8 + Streamlit Dashboard Project)**

This guide is a script you can follow while presenting the project live.  
It explains what to say and what the audience will see.

---

## 🔧 Preparation (Before Presentation)
1. Open PowerShell in the project folder:
   ```powershell
   cd C:\Users\XXX\Desktop\bird_turbine_project
   ```

2. Activate the virtual environment:
   ```powershell
   venv\Scripts\activate
   ```

3. Generate the synthetic video (birds + turbine):
   ```powershell
   python -m src.make_synthetic_video
   ```

4. Start the dashboard:
   ```powershell
   python -m streamlit run src/app.py
   ```

---

## 🎬 Demo Script (What to Say)

### Step 1: Introduction
🗣️ *“This project demonstrates how we can use AI to protect birds from collisions with wind turbines. The dashboard you see here shows detections in real time.”*

- Show the dashboard in the browser.
- Point out the **empty video panel** and **sidebar controls**.

---

### Step 2: Choose Video Source
🗣️ *“Since I don’t have a real turbine, I generated a synthetic video of birds flying near a rotating turbine.”*

- In the sidebar, select **Synthetic: birds_synth_better.mp4**.

---

### Step 3: Start the System
🗣️ *“Now I’ll start the detection system. Watch how the turbine status changes as birds approach the rotor zone.”*

- Click **▶ Start** in the sidebar.

The video begins playing with bounding boxes on detected birds.

---

### Step 4: Explain Overlays
🗣️ *“The blue box represents the rotor sweep zone. If a bird enters this area, the system marks it as a risk.”*

- Show a bird entering the blue box.
- Point out the **banner alert** (“BIRD RISK — TURBINE STOP”).

---

### Step 5: Turbine Simulation
🗣️ *“The turbine state is shown in the top-right LED. Green means RUN, Red means STOP. This simulates what would happen in a real turbine control system.”*

- Show the LED switching colors.

---

### Step 6: Charts & Logs
🗣️ *“Below, the chart shows how many birds were detected over time, and when the turbine was stopped. The event table on the side keeps a record of the most recent detections and actions.”*

- Scroll down to show the line chart and logs updating.

---

### Step 7: Wrap-Up
🗣️ *“This system could be improved with real-world training data, multiple cameras, or radar. But even with synthetic demos, we can see how AI helps balance renewable energy with wildlife protection.”*

---

## ✅ Demo Checklist
- [ ] Synthetic video generated (`birds_synth_better.mp4` exists).  
- [ ] Streamlit app launched successfully.  
- [ ] Sidebar source set to **Synthetic**.  
- [ ] Press **▶ Start** to run detection.  
- [ ] Show:
  - Bounding boxes
  - Rotor sweep zone
  - STOP/ RUN LED
  - Banner alerts
  - Chart and logs  
