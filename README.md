# Invoice Email Reminder Automation with n8n

Automate your invoice follow-ups effortlessly with n8n! This project streamlines the process of reminding clients about outstanding payments, thanking those who have paid, and updating records in real-time.

![Invoice Payment Reminder Cover](./images/Invoice%20Payment%20Reminder%20Cover.png)

---

## Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
  - [Workflow Steps](#workflow-steps)
- [Benefits](#benefits)
- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
  - [1. Clone or Import Workflow](#1-clone-or-import-workflow)
  - [2. Connect Google Sheets](#2-connect-google-sheets)
  - [3. Connect Gmail](#3-connect-gmail)
  - [4. Customize Email Templates](#4-customize-email-templates)
  - [5. Schedule the Trigger](#5-schedule-the-trigger)
  - [6. Test the Workflow](#6-test-the-workflow)
- [Customization](#customization)
  - [Invoice Data Sheet Structure](#invoice-data-sheet-structure)
  - [Email Message Personalization](#email-message-personalization)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

**Invoice Email Reminder Automation** is an n8n workflow designed for small businesses and freelancers. It:

- Automatically sends payment reminders or thank-you emails via Gmail
- Tracks invoice status using Google Sheets
- Marks each client once messaged to prevent duplicate communication
- Runs on a daily schedule, reducing manual follow-ups

---

## How It Works

![Invoice Payment Reminder Workflow](./images/Invoice%20Payment%20Reminder.png)

### Workflow Steps

1. **Schedule Trigger**
   - Initiates the workflow daily at a preset time

2. **Get Row(s) in Sheet**
   - Retrieves all invoice records from a specified Google Sheets document

3. **Filter Unsent Messages**
   - Filters out invoices where a reminder or thank-you email hasn't yet been sent (avoids duplicates)

4. **Switch (Invoice Status Check)**
   - Evaluates the payment status for each invoice: Unpaid, Partial Paid, or Paid

5. **Send Email via Gmail**
   - **Unpaid:** Sends a reminder message
   - **Partial:** Sends a partial payment reminder
   - **Paid:** Sends a thank-you message

6. **Update Sheet**
   - After sending, updates the Google Sheets row to mark the message as sent

---

## Benefits

- **Saves time** on routine follow-ups
- **Keeps clients informed** of payment status
- **Avoids duplicate emails** by updating the sheet after each send
- **Streamlines billing communications** for small businesses

---

## Requirements

- [n8n](https://n8n.io/) installation or cloud account
- Google account with:
  - Access to Google Sheets (your invoice tracker)
  - Access to Gmail (for sending emails)
- Invoice data in Google Sheets

---

## Setup Instructions

### 1. Clone or Import Workflow

- Download or import the attached workflow in your n8n instance (Visual editor or Desktop)

### 2. Connect Google Sheets

- Add your Google Sheets credentials in n8n
- Set the sheet ID and worksheet name
- Sheet must contain columns for invoice details, client email, status, and "Message Sent" marker

### 3. Connect Gmail

- Add your Gmail credentials to the email nodes in n8n
- Make sure "Send email" actions use your preferred Gmail account

### 4. Customize Email Templates

- Edit the "Send Message" nodes with your preferred text for Reminders and Thank-You notes
- Use n8n data expressions for personalization, e.g. `{{ $json["Client Name"] }}`, `{{ $json["Invoice Amount"] }}`, etc.

### 5. Schedule the Trigger

- Adjust the schedule node for your preferred run time
- Daily morning triggers are recommended

### 6. Test the Workflow

- Run the workflow manually for the first time
- Review Gmail sent folder and Google Sheet updates
- Ensure only unsent messages are triggered

---

## Customization

### Invoice Data Sheet Structure

Your sheet should look similar to the `Invoice Data.csv` file in the `data` folder.

![Invoice Spreadsheet Example](./images/Invoice%20Spreadsheet.png)

- **Status**: Values can be "Unpaid", "Partial", "Paid"
- **Message Sent**: "Yes" or "No"

### Email Message Personalization

You can personalize email subject and body using sheet columns, e.g.

**Subject**: `Payment Reminder for Invoice #{{ $json["Invoice Number"] }}`

**Body**:
```
Hi {{ $json["Client Name"] }},

This is a reminder regarding your invoice #{{ $json["Invoice Number"] }} of ${{ $json["Invoice Amount"] }} due {{ $json["Due Date"] }}.
```

---

## Troubleshooting

- **Google Sheets node fails**: Check API permissions and sheet ID
- **Gmail node errors**: Verify authentication; check if account allows API sending
- **Duplicate emails**: Confirm "Message Sent" column updates properly
- **Workflow not triggering**: Review schedule settings; check n8n instance status

---

## Contributing

Contributions and suggestions are welcome!  
Fork the repo, submit issues, or create pull requests for workflow improvements.

---

## License

This project is licensed under the MIT License.

---

## Contact

- **Email:** nebeyoumusie@gmail.com
- **LinkedIn:** [LinkedIn](https://www.linkedin.com/in/nebeyou-musie)
- **X(Twitter):** [X](https://x.com/NebeyouMusie)
- **Upwork:** [Upwork](https://www.upwork.com/freelancers/~017ff01729e3cd26e0?mp_source=share)
- **My Agency:** [Fuzion Tech Website](https://fuzion-tech.com/) or [Fuzion Tech on Upwork](https://www.upwork.com/agencies/1948388369189366041/)

---

**Skills & Technologies:**  
`n8n`, `Invoice Automation`, `Gmail integration`, `Google Sheets Automation`

---

**Enjoy automated invoice reminders and streamlined client communication!**

---

> _For any issues, please contact the project maintainer or open an issue on your workflow repository._
