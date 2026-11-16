# System Architecture

## Overview

The AI Workflow Automation project uses n8n to orchestrate an automated customer service triage process.

The workflow receives customer messages, processes them using Google Gemini, extracts structured information through JavaScript, and stores the results in Google Sheets.

## Architecture Diagram

```text
Customer
   |
   v
n8n Form Trigger
   |
   v
Basic LLM Chain <--- Google Gemini Chat Model
   |
   v
JavaScript Code
   |
   v
Google Sheets
```

## Workflow Components

### 1. Form Trigger

Receives customer messages through an n8n form.

The form contains a required text field for submitting the message.

### 2. Google Gemini Chat Model

Provides the language model used by the Basic LLM Chain.

It analyzes the submitted message according to the instructions defined in the system prompt.

### 3. Basic LLM Chain

Responsible for orchestrating the AI analysis.

It identifies:
- Customer service category.
- Customer sentiment.
- Urgency level.
- Suggested response in Portuguese.

### 4. JavaScript Code

Processes the AI-generated response and extracts the relevant information.

The data is organized into structured fields before being sent to the spreadsheet.

### 5. Google Sheets

Receives and stores the processed information.

Each execution adds a new row containing the date, original message, category, sentiment, urgency and suggested response.

## Data Flow

1. A customer submits a message through the form.
2. The message is sent to the Basic LLM Chain.
3. Google Gemini analyzes the message.
4. The AI-generated response is processed by JavaScript.
5. The structured information is appended to Google Sheets.

## Security and Limitations

- The project uses simulated customer messages.
- No real banking system integration is implemented.
- The AI does not execute financial operations.
- Generated responses are suggestions and require human review.
- API credentials must be configured separately in n8n.
- Sensitive information must not be included in public repositories.

## Technologies

- n8n
- Google Gemini
- JavaScript
- Google Sheets
- Generative AI
- Prompt Engineering
