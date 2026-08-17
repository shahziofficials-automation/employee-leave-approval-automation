# Employee Leave Approval Automation

An automated employee leave management and approval system built with **n8n, Google Forms, Google Sheets, Gmail, Webhooks, and JavaScript**.

This system automates the complete employee leave approval process — from submitting a leave request to approval/rejection and final employee notification.

---

## 📌 Project Overview

The Employee Leave Approval Automation is designed to reduce manual HR work and simplify the leave management process.

The system automatically:

- Collects employee leave requests
- Generates a unique Request ID
- Calculates leave duration
- Routes requests based on leave duration
- Sends approval requests to Manager or HR
- Processes Approve/Reject actions through Webhooks
- Updates the leave record in Google Sheets
- Notifies the employee about the final decision

---

## 🔄 Workflow Architecture

### Workflow 1 — Leave Request & Approval Routing

Employee submits leave request  
↓  
Google Forms  
↓  
Google Sheets  
↓  
n8n Google Sheets Trigger  
↓  
Extract Request Data  
↓  
Generate Request ID  
↓  
Calculate Leave Days  
↓  
Approval Routing  
↓  
Manager / HR Approval  
↓  
Approval Email

---

### Workflow 2 — Approval Processing

Approver clicks Approve / Reject  
↓  
n8n Webhook  
↓  
Extract Request ID & Action  
↓  
Find Leave Request in Google Sheets  
↓  
Check Approval Decision  
↓  
Update Leave Status  
↓  
Record Approval Information  
↓  
Notify Employee

---

## ⚙️ Workflow 1 — Leave Request Processing

### Step 1: Employee Submits Leave Request

The employee submits a leave request through a Google Form.

The form collects information such as:

- Employee Name
- Employee Email
- Department
- Leave Type
- Start Date
- End Date
- Reason
- Manager

---

### Step 2: Google Sheets Trigger

Each submitted form response is stored in Google Sheets.

The n8n Google Sheets Trigger monitors the spreadsheet and starts the automation when a new leave request is added.

---

### Step 3: Generate Unique Request ID

A JavaScript Code node generates a unique Request ID for each leave request.

Example:

`LR-20260817-4821`

This Request ID is used to track the request throughout the approval process.

---

### Step 4: Calculate Leave Days

The workflow calculates the total number of leave days using the Start Date and End Date.

Example:

Start Date: 20 August  
End Date: 22 August  

Total Leave Days: 3

---

### Step 5: Update Google Sheets

The generated Request ID and request status are written back to the corresponding Google Sheets record.

This keeps the leave request information centralized and trackable.

---

### Step 6: Approval Routing

The workflow uses conditional logic to determine the appropriate approver.

**Leave Days ≤ 2**

→ Manager Approval

**Leave Days > 2**

→ HR Approval

---

### Step 7: Approval Email

The assigned approver receives an email containing the relevant leave request details.

The email includes:

- Request ID
- Employee Name
- Leave Type
- Start Date
- End Date
- Leave Duration
- Reason
- Approve action
- Reject action

---

## 🔗 Workflow 2 — Webhook Approval Processing

When the approver clicks **Approve** or **Reject**, the action is sent to an n8n Webhook.

The Webhook receives information such as:

- Request ID
- Action
- Approver Role

Example:

`requestId = LR-20260817-4821`

`action = approve`

`role = manager`

---

## 🧠 Approval Decision Logic

### If Approved

The workflow:

1. Finds the corresponding leave request
2. Updates the status to **Approved**
3. Records the approval date
4. Records the approver role
5. Sends an approval notification to the employee

### If Rejected

The workflow:

1. Finds the corresponding leave request
2. Updates the status to **Rejected**
3. Records the review date
4. Records the approver role
5. Sends a rejection notification to the employee

---

## 📊 Google Sheets Tracking

Google Sheets is used as the centralized leave request database.

The system can track:

| Field | Purpose |
|---|---|
| Employee Name | Employee identification |
| Employee Email | Employee notification |
| Department | Employee department |
| Leave Type | Type of leave |
| Start Date | Leave start date |
| End Date | Leave end date |
| Manager | Assigned manager |
| Status | Current approval status |
| Request ID | Unique request identifier |
| Approved Date | Approval/review timestamp |
| Approved By | Approver role |
| Employee Notified | Notification tracking |

---

## 🛠️ Technologies Used

- **n8n** — Workflow automation
- **Google Forms** — Leave request collection
- **Google Sheets** — Data storage and tracking
- **Gmail** — Approval and notification emails
- **Webhooks** — Approval decision processing
- **JavaScript** — Request ID generation and leave-day calculation

---

## ✨ Key Features

- Automated leave request processing
- Unique Request ID generation
- Automatic leave-day calculation
- Conditional approval routing
- Manager and HR approval logic
- Email-based approval actions
- Webhook-based decision processing
- Automated Google Sheets updates
- Employee approval/rejection notifications
- Centralized leave request tracking

---

## 📂 Project Files

- `Workflow 1.png` — Main Leave Request & Approval Workflow
- `Workflow 2.png` — Approval Webhook & Notification Workflow
- `Leave Approval System1.json` — Main n8n Leave Approval Workflow
- `Leave Approval System2.json` — Webhook-Based Approval Processing Workflow

---

## 📸 Workflow Screenshots

### Workflow 1

![Workflow 1](Workflow%201.png)

### Workflow 2

![Workflow 2](Workflow%202.png)

---

## 🎯 Business Value

This automation reduces manual HR workload and provides a structured process for handling employee leave requests.

### Benefits

- Reduces manual administrative work
- Speeds up leave approval
- Centralizes leave records
- Improves approval tracking
- Reduces communication delays
- Standardizes the leave approval process

---

## 🔐 Security

The workflow files included in this repository are sanitized portfolio versions.

Production credentials, API keys, OAuth tokens, private webhook URLs, and confidential business information have been removed or replaced with placeholders.

Credentials and connection details should be configured separately when deploying the workflow in an n8n environment.

---

## 🚀 Future Improvements

Possible future enhancements include:

- Multi-level approval workflows
- Slack or Microsoft Teams notifications
- Automatic leave balance checking
- Weekend and holiday calculation
- Approval reminders
- HR reporting dashboard
- Role-based access control
- HR management system integration

---

## 👨‍💻 Project Summary

**Employee Leave Approval Automation**

A practical business process automation project demonstrating workflow orchestration, conditional logic, JavaScript processing, Google Workspace integration, email automation, and webhook-based approval handling using n8n.
