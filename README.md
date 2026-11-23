# AI-Powered Customer Support Workflow

An AI-powered customer support automation workflow built with **n8n** and **Google Gemini**. The workflow processes incoming customer messages, classifies them by category and urgency, stores the results in Google Sheets, and sends internal email notifications for urgent requests.

## Workflow Overview

![Workflow Overview](screenshots/workflow-overview.png)

## Features

- **Form Submission:** Receives customer information and messages through an n8n form trigger.
- **AI-Powered Classification:** Uses Google Gemini to analyze incoming messages and classify them into three categories: Sales, Service, and Other.
- **Priority Detection:** Identifies whether a request is Urgent or Regular based on its content.
- **Structured Output:** Uses the Structured Output Parser to ensure consistent and structured AI responses.
- **Data Storage:** Records original customer messages and processed information in Google Sheets.
- **Urgent Request Notifications:** Sends an internal email notification when an urgent request is identified.
- **Suggested Responses:** Generates AI-powered suggested responses based on the customer's message.

## Workflow Process

1. A customer submits a message through the form.
2. The AI Agent analyzes the message using Google Gemini.
3. The request is classified by category and priority.
4. The Structured Output Parser ensures the AI response follows the expected structure.
5. The workflow checks whether the request is urgent.
6. The request is recorded in the appropriate Google Sheets branch.
7. If the request is urgent, an internal email notification is sent.

## Tech Stack

- **n8n** – Workflow automation
- **Google Gemini API** – AI-powered message analysis and classification
- **Google Sheets** – Data storage
- **Structured Output Parser** – Structured AI output
- **Email (SMTP)** – Internal notifications

## Project Structure

```text
ai-customer-support-workflow/
│
├── workflow.json
├── README.md
└── screenshots/
    └── workflow-overview.png
```

## Setup

1. Install or access an n8n instance.
2. Import `workflow.json` into n8n.
3. Configure your own Google Gemini API credentials.
4. Connect your Google Sheets account and configure the required spreadsheet.
5. Configure email credentials for internal notifications.
6. Adjust the workflow settings and test with sample customer messages.

**Note:** API credentials and account connections are not included in the exported workflow. They must be configured separately.

## Project Goal

The goal of this project was to explore how AI agents and workflow automation can be used to streamline customer support operations, improve request organization, and ensure that urgent inquiries receive timely internal attention.
## Example Results

The following examples demonstrate how the workflow processes different customer inquiries.

### Example 1: Urgent Service Request

**Input:**
> Poštovani, potreban nam je servis fiskalnog uređaja koji je prestao da radi. Hitno nam je potrebna pomoć.

| Field | Result |
|---|---|
| Category | Service |
| Priority | Urgent |
| Status | Pending urgent processing |

**Generated Response:**

> Poštovani, primili smo vaš zahtev za servis fiskalnog uređaja. Naš tehnički tim će vas kontaktirati u najkraćem mogućem roku radi dogovora o daljim koracima i izlaska na teren.

**Workflow Action:** The request is recorded in Google Sheets and an internal email notification is sent.

### Example 2: Regular Inquiry

**Input:**
> Dobar dan, želeo bih da se informišem o mogućnostima zaposlenja u vašoj kompaniji.

| Field | Result |
|---|---|
| Category | Other |
| Priority | Regular |
| Status | Pending processing |

**Generated Response:**

> Poštovana Jano, hvala vam na interesovanju za rad u našoj kompaniji. Vašu prijavu i upit smo prosledili našem HR sektoru, koji će vas kontaktirati ukoliko se otvori pozicija koja odgovara vašim kvalifikacijama.

**Workflow Action:** The request is recorded in Google Sheets for further processing.
