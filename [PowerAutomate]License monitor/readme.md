# License Monitor Documentation (Power Automate Flow)

This document describes step-by-step how the Microsoft Power Automate flow works. The flow is responsible for monitoring the expiration dates of device licenses and automatically sending email notifications to the appropriate distribution lists according to the configuration table.

## 1. Trigger

The flow is triggered based on a schedule (e.g., daily) to check the current license expiration dates.

## 2. Initial Variables

At the beginning of the flow, the following global variables are initialized:
- **TodayDate**: Example: 2025-09-09 (current date)

## 3. Retrieving Data from AllDevicesTable

The flow connects to the Excel Online file "CV licenses_23_07.xlsx", containing information about the devices. Each row stores values such as: Server Name, Host Name, IP, Device Type, License Expiration Date, Client, Days Left, and Email Sent.

## 4. Calculating Days Until Expiration

For each record, the flow calculates the number of days remaining until the license expires (the difference between TodayDate and the license expiration date).

## 5. License Status Classification

Based on the value of Daysleft, the flow assigns a classification (stamp_daysleft):
- If Daysleft &lt; 0 → 'License expired'
- If Daysleft &lt; 90 → 'License expiring soon'
- If Daysleft &gt;= 90 → 'Notification in X days'

## 6. Matching Recipients (EmailTable)

For each client and device type, the flow matches the appropriate entry from the EmailTable to determine the recipients.

## 7. Email Generation and Sending

The flow prepares the email content, using the email title and device details (Server Name, IP, Daysleft). It then sends the email to the distribution list using the Office 365 Outlook connector.

The flow checks the EmailSent column in AllDevicesTable; if the field is empty, an email is sent, and the current date is recorded in the cell. If the date already exists, the flow verifies that at least 14 days have passed since that date, ensuring that the notification is sent only once every two weeks.