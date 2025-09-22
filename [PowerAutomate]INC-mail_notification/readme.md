# Technical Documentation for Power Automate Flow

## General Information about the Flow
- **Name:** INC - mail notification
- **Type:** Microsoft.Flow/flows
- **Description:** This flow is responsible for sending email notifications to technicians based on data from an Excel file containing INC and SR tickets. It sends reminders depending on the number of days since the ticket was created.

## Connectors and Connections Used
- Excel Online (Business) (shared_excelonlinebusiness)
- Excel Online (Business) (shared_excelonlinebusiness_2)
- Office 365 Outlook (shared_office365)

## Detailed Description of the Flow Logic
- The flow is manually triggered (Button trigger).
- It retrieves data from the ticket table (INC/SR) from an Excel file.
- It retrieves configuration data from the BOTCONFIG table (technicians, managers).
- For each technician, it filters the tickets assigned to them.
- For each ticket, it checks the type (INC/SR), the number of days since creation, and the last update.
- It creates a list of tickets and generates the email content.
- It sends an email to the technician with a reminder, including the appropriate content and list of tickets.
- It sends a copy to the relevant managers (based on the assignment in BOTCONFIG).
- Additionally, it logs the sent emails to an Excel file.

## Variables and Parameters
- **TechnicianNameCONF, TechnicianEmail:** Contact details of the technician.
- **IncitentNumber, Summary, Status, Created, DaysSinceCreation:** Ticket details.
- **INCNumberArray, SRNumberArray:** Lists of tickets.
- **Manager:** Assigned manager.
- **SDM:** Service Delivery Manager.
- **EmailsArray:** List of email addresses for notifications.

## Integrations and Security
- The flow uses Excel Online and Office 365 Outlook connectors.
- Authorization is done through user connections.
- Data is processed within the Microsoft Power Platform environment.

## Summary
The flow automates the process of reminding technicians about INC and SR tickets in ServiceNow. It integrates with Excel Online and Outlook, operates based on configuration data, and dynamically generates email content. It enables centralized management of reminders and activity reporting.