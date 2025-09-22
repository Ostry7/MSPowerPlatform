# Power Automate Flow Documentation
    
## General Information about the Flow
    
- **Name:** INC-30_60_90+weekly_report-latest
- **Display Name:** INC 30_60_90 + weekly report

## Connectors Used

- **Excel Online (Business)** (shared_excelonlinebusiness)

# Detailed Flow Logic Description
## Trigger: Request
```json
{
  "metadata": {
    "operationMetadataId": "e946826b-86f7-45c0-8526-1c91c8e328ca"
  },
  "type": "Request",
  "kind": "Button",
  "inputs": {
    "schema": {
      "type": "object",
      "properties": {},
      "required": []
    }
  }
}
```

## Main Actions and Logic:
1.  Trigger: Request
2.  OpenApiConnection: SNOW\_RAPORT
3.  Initialize Variable: ticketNumber
4.  Initialize Variable: Summary
5.  Initialize Variable: Customer
6.  Initialize Variable: Severity
7.  Initialize Variable: Status
8.  Initialize Variable: CreatedBy
9.  Initialize Variable: Created
10.  Initialize Variable: Updated
11.  Initialize Variable: AssignedTo
12.  Initialize Variable: WorkNotes
13.  Expression: Current\_time
14.  Initialize Variable: CurrentDate
15.  Initialize Variable: UpdatedISO
16.  Initialize Variable: CreatedISO
17.  Initialize Variable: UpdatedConv
18.  Initialize Variable: CreatedConv
19.  Initialize Variable: UpdatedConvINT
20.  Initialize Variable: CreatedConvINT
21.  Initialize Variable: WorkNotesTechnician
22.  Initialize Variable: TechnicianBotConfig
23.  OpenApiConnection: BOTCONFIG
24.  Loop: Create\_technician\_name\_array
25.  Initialize Variable: DateFromWorkNotes
26.  Initialize Variable: WorkStart
27.  Initialize Variable: WorkStartConv
28.  Loop: CREATE\_Book.xslx\_AND\_30\_60\_90.xlsx\_FILES
29.  Initialize Variable: Offering
30.  Initialize Variable: SeverityFromSNOW
31.  Initialize Variable: ExtractDateName
32.  Initialize Variable: date
33.  Initialize Variable: name
34.  Initialize Variable: newLine
35.  SetVariable: Set\_newLine\_variable
36.  Initialize Variable: typeString
37.  SetVariable: Set\_typeString\_variable
38.  Initialize Variable: LastUpdateNew
39.  Initialize Variable: CurrentItemLen
40.  Initialize Variable: CurrentItemLenINT
41.  Initialize Variable: endString
42.  SetVariable: Set\_endString\_variable
43.  OpenApiConnection: 30\_60\_90\_RAPORT
44.  Loop: Cleanup\_AllTicketsTable\_30\_60\_90.xslx
45.  OpenApiConnection: 30\_60\_90\_RAPORT\_FRESH\_DATA
46.  Loop: Apply\_to\_each\_30\_60\_90\_FRESH\_RAPORT\_DATA
47.  Initialize Variable: Datestamp
48.  Initialize Variable: DaysSinceCreation
49.  Initialize Variable: NewCreated
50.  Initialize Variable: IncidentManagerConfig
51.  Initialize Variable: IncidentManagerName
52.  Initialize Variable: SplitComments
53.  Initialize Variable: NewestTechComment
54.  Initialize Variable: FoundTechnicianComment
55.  Delay: Delay

## Variables and Parameters

*   ticketNumber (string)
*   Summary (string)
*   Customer (string)
*   Severity (string)
*   Status (string)
*   CreatedBy (string)
*   Created (string)
*   Updated (string)
*   AssignedTo (string)
*   WorkNotes (string)
*   CurrentDate (string)
*   UpdatedISO (string)
*   CreatedISO (string)
*   UpdatedConv (string)
*   CreatedConv (string)
*   UpdatedConvINT (integer)
*   CreatedConvINT (integer)
*   WorkNotesTechnician (string)
*   TechnicianBotConfig (array)
*   DateFromWorkNotes (string)
*   WorkStart (string)
*   WorkStartConv (string)
*   Offering (string)
*   SeverityFromSNOW (string)
*   ExtractDateName (array)
*   date (string)
*   name (string)
*   newLine (string)
*   typeString (string)
*   LastUpdateNew (array)
*   CurrentItemLen (string)
*   CurrentItemLenINT (integer)
*   endString (string)
*   Datestamp (string)
*   DaysSinceCreation (string)
*   NewCreated (integer)
*   IncidentManagerConfig (array)
*   IncidentManagerName (string)
*   SplitComments (string)
*   NewestTechComment (string)
*   FoundTechnicianComment (boolean)

## Summary

The flow automates the process of reporting and classifying tickets (INC/SR) based on data from Excel Online files. It uses a series of conditions and loops to process data, classify incidents, update statuses, and generate reports. It integrates with Excel Online (Business) and operates on-demand (manual trigger).