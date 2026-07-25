# ForgeMind Hackathon Demo Video Script (2 Minutes Max)

This script is structured second-by-second to directly address the judging criteria: **Technical Quality (25%)**, **Innovation (25%)**, **Real-World Impact (20%)**, and **Completeness (10%)**.

---

## ⏱️ Video Breakdown

| Time | Visual on Screen | Voiceover (What to Read Aloud) | Judging Focus |
| :--- | :--- | :--- | :--- |
| **0:00 - 0:20** | **ForgeMind Dashboard** (Start on the landing page showing the clean, white light theme and the Machine Radar grid). Click on the first machine. | *"In modern manufacturing, unexpected machinery downtime costs factories billions. Meet **ForgeMind**—an autonomous factory maintenance and diagnostics platform built on NitroStack MCP. We’ve designed a premium, light-themed engineering workspace featuring live telemetry feeds and interactive digital twin CAD blueprints."* | **Real-World Impact** & **Aesthetics** |
| **0:20 - 0:45** | **CAD Blueprint Visualizer** (Scroll to the isometric blueprint of the CNC Mill. Toggle through the layer controls: **Outer Shell**, **Internal Core**, **Sensors**). *Make sure to point out the spinning chuck tool!* | *"At the heart of the interface is our **Dynamic CAD Blueprint**. Engineers can inspect components across layers—from the Outer Frame to the Internal Mechanical Core and telemetry probes. Notice the live visual animations: our tools spin, and hydraulic fluid pulses actively, changing dynamically based on machine states."* | **Innovation & Creativity** |
| **0:45 - 1:15** | **Fault Injection & MCP Log Console** (Click on the **Demo Lab** tab. Click **Inject Fault** on the **CNC Spindle Bearing Fault** scenario. Observe the live log terminal stream logs in real-time). | *"Let's inject a simulated bearing wear fault. Instantly, our FastAPI gateway detects the anomaly and initiates an **Autonomous MCP Agent Loop**. Running dynamically over our custom **forgemind-mcp-server**, the AI agent executes tools like `get_machine_history` and `retrieve_sop` via Standard I/O to isolate the root cause, streaming every step in real-time over WebSockets."* | **Technical Quality & Completeness** |
| **1:15 - 1:45** | **Defect Diagnostics Assistant** (Select the Spindle Bearing. View the **Defect Signature** tab showing the FFT waves, the **Stress Radar** polygon, and click the **Lockout Checklist** checkboxes). | *"Once diagnosed, the engineer is presented with an **Interactive Diagnostics console**. We can analyze the **Rotational Defect Signature** showing healthy baseline harmonics versus active vibration spikes, inspect the component's **Stress Radar**, and tick off the step-by-step physical **Lockout/Tagout safety checklist** before starting repair."* | **Innovation & Completeness** |
| **1:45 - 2:00** | **Full Dashboard View** (Zoom out showing the finished work order, the nominal status of the mill, and the clean styling). | *"By connecting custom TypeScript MCP schemas, FastAPI websocket streams, and rich interactive visuals, ForgeMind turns raw telemetry into safe, instant, actionable maintenance insights. Thank you."* | **Presentation & Storytelling** |

---

## 💡 Quick Tips for Recording:
1. **Resolution**: Record at full screen (1080p).
2. **Speed**: Click slowly and deliberately. When you toggle a tab or inject a fault, give the UI 1–2 seconds to update so the judges can follow the action.
3. **Audio**: Use a clear microphone and speak in a confident, professional engineering tone.
