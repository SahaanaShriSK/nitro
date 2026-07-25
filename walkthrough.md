# ForgeMind Premium Light-Mode & CAD Twin Walkthrough

The ForgeMind platform has been completely redesigned from the typical dark/neon layout into a clean, high-end light theme. It features a technical slate dot-grid CAD background and a single primary accent: **Peacock Blue** (`#0e7490`). 

An interactive **CAD Digital Twin Schematic Visualizer** has also been implemented in the Command Center dashboard, showing live machine internals, layer selectors, and real-time warning hotspots.

---

## Technical Features Implemented

1. **Clean White & Peacock Blue Theme**:
   - The dark grid has been replaced by a pure white background (`#ffffff`) styled with a subtle slate-dotted blueprint pattern.
   - All primary navigation buttons, headings, and accents now use a cohesive peacock blue palette.
   - Generic AI grid styles have been converted to lightweight, clean cards with soft dropshadows (`box-shadow`) and elegant slate borders.

2. **CAD Digital Twin Blueprint Visualizer**:
   - Renders a styled CAD-like blueprint (isometric vector wireframes) for each production machine when selected.
   - Supports live machine states (including `EQ101` Spindle Assembly, `EQ103` 6-Axis Robot, `EQ107` Heavy Press) fetched from the active backend.
   - **Hotspot Highlighting**: Under fault conditions, the faulty component (e.g., Ceramic Spindle Bearings) highlights in glowing red, showing an animated warning ripple and a telemetry callout box.

3. **CAD Layer Toggles**:
   - Users can toggle between three drawing layers dynamically:
     - **Outer Shell**: Highlights structural outer casing.
     - **Internal Core**: Fades the outer casing to show internal mechanics (e.g. motors, gearboxes, bearings).
     - **Sensors & Probes**: Highlights active telemetry sensors and signal buses.

4. **Component Inspector & Spares Requisition**:
   - Clicking any part in the blueprint updates the inspector sidebar with spec details, greasing baselines, and stock checks.
   - If the part is faulty, a context-aware **"Replace Component"** button appears, allowing technicians to dispatch replacement work orders.

---

## Walkthrough Visuals

### Redesigned Peacock Blue Dashboard Overview
The new light-mode dashboard overview displaying the machine radar grid, live log events, and a clean white background theme:

![Redesigned Dashboard Overview](https://raw.githubusercontent.com/SahaanaShriSK/nitro/main/walkthrough_images/dashboard_top.png)

### Spindle Assembly CAD Schematic (Fault State)
Scrolling to the visualizer displays the active **5-Axis Spindle Assembly (Digital Twin)**. The faulty lower angular bearing turns red, calling out the telemetry breach in real-time:

![Spindle Assembly Fault Blueprint](https://raw.githubusercontent.com/SahaanaShriSK/nitro/main/walkthrough_images/spindle_fault.png)

---

## Claude's Hackathon Review Fixes (Completed)

1. **Real-time Live WebSocket Log Streaming**:
   - Replaced the decorative `/ws` endpoint with a functional connection broker (`active_connections`).
   - Wired the AI Agent loop (`orchestrator.py`) to broadcast reasoning steps and dynamic NitroStack tool execution results back to the dashboard console in real-time.
   - Connected the React frontend using `connectWebSocket` to dynamically stream these logs into the console log state.

2. **Dynamic Telemetry Mappings**:
   - Replaced hardcoded values in the `/api/machines` endpoint in `api_server.py`.
   - Telemetry now queries real measurements (vibration, temperature, status) dynamically matched from `forgemind_server/data/telemetry_logs.json`.

3. **MCP Server Refactor**:
   - Added real implementations for `get_machine_history` (parses telemetry logs) and `retrieve_sop` (returns SOP specs based on machine ID).
   - Deleted the starter boilerplate `CalculatorModule` and renamed the MCP server registry entry to `forgemind-mcp-server`.

4. **Automated Pytest API Suite**:
   - Created `forgemind_server/tests/test_api.py` validating `/health`, `/api/scenarios`, and `/api/machines` telemetry loading. Running `pytest` shows `3 passed` with 100% success.

### WebSocket Console and AI Investigation Screenshots

#### Live Gateway Log Console (Demo Lab Tab)
Shows WebSocket startup hooks connected to the live event bus:

![Live Log Console](https://raw.githubusercontent.com/SahaanaShriSK/nitro/main/walkthrough_images/log_console.png)

#### AI Investigation & Verification Chain (Active Triage)
Shows the complete 3-step dynamic tool verification chain utilizing our new tools (`get_machine_history`, `retrieve_sop`) to resolve the root cause:

![AI Investigation Triage Chain](https://raw.githubusercontent.com/SahaanaShriSK/nitro/main/walkthrough_images/triage_chain.png)

---

## Interactive Defect Signature & Diagnostics Assistant (New Feature)

To provide reliability engineers with actionable tools to explain machine defects in-depth, we built a custom **Defect Diagnostics & Troubleshooting Assistant** directly below the CAD blueprints:

1. **Rotational Defect Frequency Signature**: A live visual FFT (Fast Fourier Transform) magnitude canvas comparing the normal baseline rotation ripples (green dashed line) to the actual damaged harmonic spikes (red wave), exposing bearing wear harmonics or joint backlash.
2. **Interactive Component Stress Radar**: A radial coordinate polygon chart showing load, thermal, power, friction, and fatigue metrics based on active machine telemetry.
3. **Lockout/Tagout (LOTO) Checklist**: A step-by-step physical lockout checklist that guides technicians on PPE gear requirements and isolation procedures to safely prepare the machine for repair.

#### Defect Diagnostics Assistant (Checklist Interaction)
Renders dynamic troubleshooting steps and defect summaries based on the active machine selection:

![Defect Explainer Widget](https://raw.githubusercontent.com/SahaanaShriSK/nitro/main/walkthrough_images/defect_explainer.png)

---

## Dynamic CAD Blueprint Animations (Wow Factor)

To provide an elite user experience suitable for a national hackathon presentation, we added highly fluid, context-aware mechanical animations directly inside the isometric blueprints:
- **CNC Mill Spindle Rotation**: The chuck and drill bit spin continuously at high frequency when the machine is online, and wobble out-of-alignment with a violent vibration animation under warning or critical spindle bearing wear.
- **Hydraulic Oil Flow Pulses**: An animated dashed line representing hydraulic lines flows continuously along the robotic joints and cylinders, illustrating live system pressure and transport speed.
- **Stamping Press Cylinder Cycle**: The heavy press piston, rod, and stamp head slide down recursively to stamp and retract when online, and jam frozen in place when high pressure relief valve breaches are active.
- **Generic Impeller Rotation**: Renders an animated rotating fan blade detailing cooling system baselines.
