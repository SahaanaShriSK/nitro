# ForgeMind

### Autonomous Manufacturing Intelligence using the Model Context Protocol (MCP)

> *The AI operating layer for modern factories.*

---

# Problem Statement

Manufacturing data is spread across machine logs, SOPs, maintenance records, and inventory systems. During failures, engineers must manually search these sources to identify the root cause, causing production downtime and delayed maintenance.

### Challenges
- Scattered information across multiple systems
- Time-consuming root cause analysis
- Delayed maintenance response
- Manual work order creation
- Increased production downtime

---

# Solution

ForgeMind is an MCP-native AI platform built on NitroStack that automates machine diagnostics using AI agents. It retrieves SOPs, analyzes machine history, checks inventory, estimates production impact, and creates work orders from a single interface.

### Key Capabilities
- 🤖 AI-powered root cause analysis
- 📖 RAG-based SOP retrieval
- 📊 Machine history analysis
- 📦 Inventory verification
- 📝 Automatic work order generation
- 📉 Production impact estimation
- ⚡ Real-time monitoring dashboard

---

# Features

- AI-powered root cause analysis
- RAG-based SOP retrieval
- Machine history analysis
- Inventory verification
- Automatic work order generation
- Production impact estimation
- Interactive monitoring dashboard

---

# Architecture

```
Dashboard
     │
     ▼
Orchestrator Agent
     │
     ▼
NitroStack MCP Server
     │
 ┌───┼─────────────────────────┐
 │   │     │      │      │     │
 ▼   ▼     ▼      ▼      ▼     ▼
Machine SOP History Inventory Work Order Impact
```

---

# Multi-Agent Workflow

```text
                Machine Fault Detected
                        │
                        ▼
              Diagnosis Agent
        (Analyzes machine anomaly)
                        │
                        ▼
        ┌──────── Verification Agent ────────┐
        │ Validates diagnosis using history  │
        │ and confidence checks              │
        └────────────────┬───────────────────┘
                         │
        ┌────────────────┼────────────────────┐
        ▼                ▼                    ▼
   SOP Agent      History Agent      Inventory Agent
(Retrieve SOP) (Past failures)    (Check spare parts)
        │                │                    │
        └────────────────┴────────────────────┘
                         │
                         ▼
             Decision & Planning Agent
      (Generate repair recommendation)
                         │
                         ▼
               Work Order Agent
      (Create maintenance work order)
                         │
                         ▼
             Production Impact Agent
      (Estimate downtime & production loss)
                         │
                         ▼
          Dashboard & Engineer Notification
```



# Agent Details

## 1. Diagnosis Agent

**Role:**  
The Diagnosis Agent is the primary decision-making agent responsible for analyzing machine failures. It receives fault events from the monitoring system and identifies the most likely root cause by combining real-time machine data with historical information.

**Responsibilities**
- Detect abnormal machine behavior.
- Analyze sensor readings and fault events.
- Identify possible root causes.
- Generate an initial diagnosis with a confidence score.
- Trigger the Verification Agent for validation.

**Input**
- Machine ID
- Sensor data
- Fault codes
- Machine status

**Output**
- Suspected fault
- Root cause
- Confidence score
- Machine affected

---

## 2. Verification Agent

**Role:**  
The Verification Agent ensures that the diagnosis is accurate before any maintenance action is taken. Instead of relying on a single AI response, it cross-checks the diagnosis using historical failures, maintenance records, and retrieved documentation.

**Responsibilities**
- Validate the diagnosis.
- Compare with historical maintenance records.
- Cross-reference machine behavior with previous incidents.
- Reduce false positives.
- Approve or reject the diagnosis.

**Input**
- Initial diagnosis
- Machine history
- Previous repair records
- SOP information

**Output**
- Verified diagnosis
- Confidence level
- Suggested corrective action

---

## 3. SOP Agent

**Role:**  
The SOP Agent retrieves the most relevant Standard Operating Procedures (SOPs) and maintenance manuals using Retrieval-Augmented Generation (RAG). This helps engineers follow the correct repair procedure without manually searching through lengthy documents.

**Responsibilities**
- Search manufacturing documentation.
- Retrieve relevant maintenance procedures.
- Provide repair instructions.
- Supply safety precautions.
- Assist engineers during repairs.

**Technologies**
- Qdrant Vector Database
- FastEmbed
- RAG Pipeline

**Input**
- Machine ID
- Fault type

**Output**
- Relevant SOP
- Repair steps
- Safety instructions

---

## 4. History Agent

**Role:**  
The History Agent analyzes previous machine failures and maintenance activities to identify recurring issues and similar fault patterns.

**Responsibilities**
- Retrieve historical fault records.
- Identify recurring failures.
- Compare current issue with previous incidents.
- Estimate repair frequency.
- Provide maintenance insights.

**Input**
- Machine ID

**Output**
- Previous failures
- Repair history
- Failure trends
- Similar incidents

---

## 5. Inventory Agent

**Role:**  
The Inventory Agent verifies whether the required spare parts are available before maintenance begins. This prevents unnecessary delays caused by unavailable components.

**Responsibilities**
- Check spare-part availability.
- Verify stock levels.
- Identify missing components.
- Recommend alternative parts if available.

**Input**
- Part ID
- Required components

**Output**
- Availability status
- Quantity in stock
- Required procurement

---

## 6. Decision Agent

**Role:**  
The Decision Agent acts as the orchestrator that combines outputs from all other agents and produces the final maintenance recommendation.

Instead of depending on a single source, it considers machine history, SOP recommendations, inventory status, and the verified diagnosis to determine the best repair strategy.

**Responsibilities**
- Aggregate information from all agents.
- Prioritize repair actions.
- Generate maintenance recommendations.
- Decide whether immediate shutdown is required.
- Prepare final maintenance summary.

**Input**
- Verified diagnosis
- SOP recommendations
- Machine history
- Inventory status

**Output**
- Final repair recommendation
- Repair priority
- Maintenance summary

---

## 7. Work Order Agent

**Role:**  
Once the repair strategy is finalized, the Work Order Agent automatically creates a maintenance work order containing all necessary repair information.

**Responsibilities**
- Generate maintenance ticket.
- Assign issue description.
- Include repair recommendations.
- Record machine details.
- Store work order in the database.

**Input**
- Machine ID
- Verified diagnosis
- Repair recommendation

**Output**
- Work Order ID
- Maintenance ticket
- Repair summary

---

## 8. Production Impact Agent

**Role:**  
The Production Impact Agent estimates how the machine failure affects production by calculating downtime, production loss, and operational impact.

This helps maintenance teams prioritize repairs based on business impact.

**Responsibilities**
- Estimate downtime.
- Calculate production loss.
- Predict operational impact.
- Prioritize high-impact failures.
- Support maintenance planning.

**Input**
- Machine ID
- Estimated repair duration

**Output**
- Downtime estimate
- Production loss
- Business impact
- Repair priority


# MCP Tools

- `find_machine(machine_id)`
- `retrieve_sop(machine_id)`
- `get_machine_history(machine_id)`
- `check_inventory(part_id)`
- `create_work_order(machine_id, issue_summary)`
- `estimate_production_impact(machine_id, downtime_min)`

---

# Tech Stack

- **Frontend:** React, TypeScript
- **Backend:** NitroStack MCP SDK
- **Database:** MongoDB
- **Vector Database:** Qdrant
- **Embeddings:** FastEmbed
- **AI:** LLM + RAG
- **Real-time:** WebSockets, Redis

---

# Workflow

1. Detect machine fault
2. Retrieve machine details
3. Search relevant SOP
4. Analyze maintenance history
5. Check spare-part availability
6. Estimate production impact
7. Generate work order

---

# Demo Scenarios

- Bearing Failure
- Machine Overheating
- Spare-Part Shortage

---

# Future Scope

- Predictive maintenance
- Multi-factory deployment
- Technician scheduling
- ERP integration
- IoT sensor connectivity

---
