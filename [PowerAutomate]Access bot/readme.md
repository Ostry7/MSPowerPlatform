# BOT Server L1/L2

## General Information
This project is a Power Automate Flow designed to automate the process of monitoring and notifying about password expirations for L1 and L2 users.

## Connectors and Connections Used
- **Excel Online (Business)**: API: `/providers/Microsoft.PowerApps/apis/shared_excelonlinebusiness`
- **Office 365 Outlook**: API: `/providers/Microsoft.PowerApps/apis/shared_office365`

## Detailed Flow Logic
- **Trigger**: Recurrence (Frequency: Day, Interval: 1, Start: 2022-10-17T09:00:00Z)
- **Main Steps**:
  - Initialize variables: `var_personL2`, `var_clientNameL2`, `var_DayLeftBOTConfigL2`, `var_mailL2`, `var_DaysLeftZertoTableL2`, `var_notificationStatusL2`, `var_vendorL2`, `var_personL1`, `var_clientNameL1`, `var_DayLeftBOTConfigL1`, `var_DaysLeftZertoTableL1`, `var_mailL1`, `var_notificationStatusL1`, `var_vendorL1`
  - Fetch records from Excel: `List_rows_Accesses_Status_L2`, `List_rows_Accesses_Status_L1`
  - Loop through each record: `Apply_to_each_L2`, `Apply_to_each_L1`
  - Fetch data: Name, Client, Vendor, Email, Notification Status, Days Left
  - Calculate notification threshold
  - Send email notifications based on conditions:
    - If notification status is ON and Days Left &lt;= threshold and &gt; 0: Send email "password will expire in X days"
    - If notification status is ON and Days Left = 0: Send email "password has expired"
    - If notification status is ON and Days Left = -1: Send email "password has expired"

## Variables and Parameters
- `personL2` (string)
- `clientNameL2` (string)
- `DayLeftBOTConfigL2` (string)
- `mailL2` (string)
- `DaysLeftZertoTableL2` (string)
- `notificationStatusL2` (string)
- `vendorL2` (string)
- `personL1` (string)
- `clientNameL1` (string)
- `DayLeftBOTConfigL1` (string)
- `DaysLeftZertoTableL1` (string)
- `mailL1` (string)
- `notificationStatusL1` (string)
- `vendorL1` (string)

## Summary
The flow automates the process of monitoring and notifying about password expirations for L1 and L2 users. It integrates with Excel Online and Office 365 Outlook, operates cyclically and autonomously, with the possibility of expansion to include additional conditions and communication channels.