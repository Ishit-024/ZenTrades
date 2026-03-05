<p align="center">

# Automation Pipeline


</p>

<p align="center">

![Automation](https://img.shields.io/badge/Automation-n8n-blue)
![Infrastructure](https://img.shields.io/badge/Infrastructure-Zero--Cost-green)
![Storage](https://img.shields.io/badge/Data-Structured_JSON-orange)
![Versioning](https://img.shields.io/badge/Version-Controlled-purple)
![Status](https://img.shields.io/badge/Assignment-Zentrades-success)

</p>

---
## 🎥 Project Walkthrough (Video Demo)

To make the workflow and automation pipeline easier to understand, I have recorded a short **visual walkthrough** explaining the pipeline execution. 
<p align="center">
  <a href="https://www.loom.com/share/c58d35e36fbd4484b0b758e69f318f2a">
    <img src="https://cdn.loom.com/sessions/thumbnails/c58d35e36fbd4484b0b758e69f318f2a-with-play.gif" width="700">
  </a>
</p>

**Watch the full demo here:**  
https://www.loom.com/share/c58d35e36fbd4484b0b758e69f318f2a
# Overview

This repository contains my implementation of the **Clara Answers Automation Assignment** submitted for **Zentrades**.

The system demonstrates how conversational business data can be transformed into **structured AI receptionist configurations** using an automated pipeline.

The workflow processes:

• **Demo call transcripts**  
• **Onboarding updates**

and automatically generates:

• Structured **Account Memo JSON**  
• **Retell AI agent configurations**  
• **Version updates (v1 → v2)**  
• **Change tracking logs**

The project is designed to behave like a **small automation product**, focusing on:

- Reproducibility
- Clear structure
- Version tracking
- Zero-cost infrastructure

---

# Core Objective

Build an automation system that:

1. Extracts business information from demo calls
2. Generates an initial **Retell AI receptionist configuration**
3. Stores structured artifacts for each account
4. Processes onboarding updates
5. Updates the AI agent configuration
6. Tracks changes through versioning and changelogs

---

# System Architecture

The automation system consists of **two major pipelines**.

---

## Pipeline A  
### Demo Call → Agent Draft

**Input**

Demo call transcript

**Output**

- Account Memo JSON
- Retell Agent Draft Spec (v1)
- Stored account artifacts

**Steps**

1. Transcript ingestion
2. Data normalization
3. Information extraction
4. Account memo generation
5. Agent configuration creation
6. Artifact storage

---

## Pipeline B  
### Onboarding Update → Agent Revision

**Input**

- Onboarding transcript
- Onboarding form

**Output**

- Updated Account Memo JSON (v2)
- Updated Retell Agent Spec (v2)
- Changelog

**Steps**

1. Onboarding input ingestion
2. Update extraction
3. Memo patching
4. Agent regeneration
5. Versioned storage
6. Change tracking

---
## System Architecture Overview

The following diagram illustrates the full automation lifecycle,
from demo call processing to agent configuration updates and
versioned change tracking.

## Workflow Architecture

The automation pipeline processes demo call transcripts and onboarding updates to generate and maintain versioned Retell AI agent configurations.

```
                +------------------------+
                |   Demo Call Transcript |
                +-----------+------------+
                            |
                            v
              +-----------------------------+
              |  Transcript Processing      |
              |  - Parsing                  |
              |  - Cleaning                 |
              |  - Normalization            |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Structured Data Extraction |
              |  (Generate Business JSON)   |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Account Memo Generator     |
              |  (Business Knowledge Base)  |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Retell Agent Spec Builder  |
              |  Initial AI Receptionist    |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Account Artifact Storage   |
              |  Versioned Config (v1)      |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Onboarding Transcript/Form |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Update Extraction Layer    |
              |  Detect New Information     |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Config Regeneration        |
              |  Updated Memo + Agent (v2)  |
              +-------------+---------------+
                            |
                            v
              +-----------------------------+
              |  Changelog Generator        |
              |  Track Differences v1 → v2  |
              +-----------------------------+
```

# Tech Stack

| Component | Technology |
|--------|--------|
| Automation | **n8n (Self-hosted)** |
| Storage | **Local JSON files** |
| Version Control | **GitHub** |
| Processing | **Prompt templating + structured extraction** |
| Optional Transcription | **Whisper (local)** |

All infrastructure follows the **zero-cost constraint** of the assignment.

---

## Repository Structure

The repository is organized to clearly separate datasets, automation workflows, generated artifacts, and helper utilities.

```
ZenTrades/
│
├── workflows/
│   └── n8n_workflow.json
│       # n8n automation workflow responsible for orchestrating the entire pipeline
│
├── dataset/
│   │
│   ├── demo_calls/
│   │   └── demo_call_1.txt
│   │       # Demo call transcripts used to generate initial agent configurations
│   │
│   └── onboarding_calls/
│       └── onboarding_call_1.txt
│           # Onboarding transcripts or forms used to update configurations
│
├── outputs/
│   │
│   └── accounts/
│       │
│       └── <account_id>/
│           │
│           ├── v1/
│           │   ├── account_memo.json
│           │   │   # Structured business information extracted from demo calls
│           │   │
│           │   └── agent_spec.json
│           │       # Initial Retell AI receptionist configuration
│           │
│           └── v2/
│               ├── account_memo.json
│               │   # Updated business memo generated after onboarding updates
│               │
│               └── agent_spec.json
│                   # Revised AI receptionist configuration
│
├── changelog/
│   └── <account_id>_changes.json
│       # Tracks modifications between agent configuration versions
│
├── scripts/
│   └── helper_scripts.js
│       # Utility scripts used for preprocessing, formatting, or workflow support
│
└── README.md
    # Documentation explaining architecture, setup, and usage
```

# Account Memo Format

The system generates a structured memo for each business.

```json
{
  "account_id": "",
  "company_name": "",
  "business_hours": {
    "days": "",
    "start": "",
    "end": "",
    "timezone": ""
  },
  "office_address": "",
  "services_supported": [],
  "emergency_definition": [],
  "emergency_routing_rules": {},
  "non_emergency_routing_rules": {},
  "call_transfer_rules": {},
  "integration_constraints": [],
  "after_hours_flow_summary": "",
  "office_hours_flow_summary": "",
  "questions_or_unknowns": [],
  "notes": ""
}

Retell Agent Draft Spec

Each account produces a Retell AI configuration.{
  "agent_name": "",
  "voice_style": "",
  "system_prompt": "",
  "key_variables": {},
  "tool_invocation_placeholders": {},
  "call_transfer_protocol": "",
  "fallback_protocol": "",
  "version": "v1"
}

Changelog Example:
{
  "account_id": "ACME001",
  "changes": [
    "Updated business hours",
    "Added emergency routing contact",
    "Updated services supported"
  ]
}

## Running the Project Locally

Follow the steps below to reproduce the automation pipeline on your machine.

---

### 1. Clone the Repository

```bash
git clone https://github.com/Ishit-024/ZenTrades.git
cd ZenTrades
```

---

### 2. Install Docker (Required)

This project runs the **n8n automation engine** using Docker.

Download Docker Desktop:

https://www.docker.com/products/docker-desktop

Verify installation:

```bash
docker --version
```

---

### 3. Start the n8n Automation Server

Run the following command:

```bash
docker run -it --rm \
-p 5678:5678 \
-v ~/.n8n:/home/node/.n8n \
n8nio/n8n
```

Once the container starts, open your browser and go to:

```
http://localhost:5678
```

This will open the **n8n workflow dashboard**.

---

### 4. Import the Workflow

Inside the n8n interface:

1. Click **Workflows**
2. Click **Import Workflow**
3. Upload the workflow file:

```
workflows/n8n_workflow.json
```

This workflow contains the **automation pipeline for transcript processing and agent configuration generation**.

---

### 5. Add Transcript Dataset

Place transcript files inside the dataset directory.

```
dataset/
│
├── demo_calls/
│   └── demo_call_1.txt
│
└── onboarding_calls/
    └── onboarding_call_1.txt
```

Each transcript represents **one customer interaction**.

---

### 6. Execute the Workflow

Trigger the workflow inside **n8n**.

The pipeline will automatically perform:

- Transcript processing
- Business information extraction
- Account memo generation
- Retell agent configuration generation
- Version updates after onboarding changes
- Changelog generation

---

### 7. View Generated Outputs

All generated artifacts are stored in:

```
outputs/
│
└── accounts/
    └── <account_id>/
        ├── v1/
        │   ├── account_memo.json
        │   └── agent_spec.json
        │
        └── v2/
            ├── account_memo.json
            └── agent_spec.json
```

- **v1** is generated from the **demo call transcript**
- **v2** is generated after **processing onboarding updates**

---

### 8. Check Change Logs

All detected updates between versions are stored in:

```
changelog/
```

Example file:

```
ACME001_changes.json
```

This file lists the **differences between the v1 and v2 configurations**.

---

### 9. Optional: Retell Agent Setup

If Retell API access is unavailable:

1. Create a Retell account
2. Copy the generated `agent_spec.json`
3. Paste the configuration manually inside the Retell dashboard

The generated specification follows the **Retell agent configuration format**.

## Future Improvements

Possible extensions to this system include:

- Direct **Retell API integration** for automatic agent deployment
- Automatic **call transcript ingestion from call recording systems**
- Real-time **workflow triggers using webhooks**
- Advanced **semantic change detection** between transcript versions
- UI dashboard for **account configuration monitoring**

---

## Author

**Ishit Setia**

This project was developed as part of the **automation pipeline assignment for Zentrades**, demonstrating workflow orchestration, transcript intelligence, and configuration versioning using n8n.
