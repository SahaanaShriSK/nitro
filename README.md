# ForgeMind

AI-powered Manufacturing Intelligence Platform built using the NitroStack Model Context Protocol (MCP).

## Overview

ForgeMind is an intelligent manufacturing assistant that helps factories reduce downtime, streamline maintenance, and improve operational efficiency through AI-driven decision support.

Using the Model Context Protocol (MCP), the platform enables AI agents to interact with manufacturing data through structured tools, providing maintenance recommendations, machine diagnostics, inventory insights, and production impact analysis.

## Features

- Predictive machine diagnostics
- Machine information retrieval
- Standard Operating Procedure (SOP) lookup
- Maintenance history tracking
- Spare parts inventory checking
- Automated work order creation
- Production impact estimation
- MCP-native AI tool integration

## MCP Tools

| Tool | Description |
|------|-------------|
| `find_machine()` | Retrieve machine information using Machine ID |
| `retrieve_sop()` | Fetch the Standard Operating Procedure for a machine |
| `get_machine_history()` | View maintenance and service history |
| `check_inventory()` | Check availability of spare parts |
| `create_work_order()` | Generate maintenance work orders |
| `estimate_production_impact()` | Estimate production loss due to downtime |

## Tech Stack

### Backend
- TypeScript
- Node.js
- NitroStack MCP SDK
- MongoDB
- Mongoose
- Zod

### Frontend
- React
- Vite
- TypeScript

### AI
- MCP Tool Calling
- LLM Integration
- Retrieval-Augmented Responses (RAG)

## Project Structure

```
ForgeMind/
│
├── forgemind-dashboard/      # React Dashboard
├── forgemind_server/         # Backend APIs
├── nitrostack-mcp-server/    # MCP Server
└── README.md
```

## Installation

Clone the repository

```bash
git clone <repository-url>
cd ForgeMind
```

Install dependencies

```bash
npm install
```

Run the development server

```bash
npm run dev
```

## Example Workflow

1. User reports a machine issue.
2. AI identifies the machine.
3. Maintenance history is retrieved.
4. SOP is fetched.
5. Spare part inventory is checked.
6. A work order is created.
7. Production impact is estimated.

## Use Cases

- Manufacturing Plants
- Smart Factories
- Industrial Automation
- Predictive Maintenance
- Equipment Monitoring
- Industry 4.0 Applications

## Future Enhancements

- Real-time IoT sensor integration
- Predictive failure forecasting
- Multi-factory analytics dashboard
- Automated maintenance scheduling
- Digital Twin integration

## Team

- Nethra R
- Sahaana Shri
- Harini
- Sandy

## Built For

NitroStack MCP Hackathon

---

Empowering intelligent manufacturing through AI and the Model Context Protocol.
