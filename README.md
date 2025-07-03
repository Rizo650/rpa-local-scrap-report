# Local Scrap Report Notification - UiPath RPA

This RPA project automates the daily retrieval of Local Scrap dispatch data from a SQL database and sends a structured text summary via **WhatsApp Web UI automation**. Built with UiPath's REFramework, it ensures modularity, error handling, and daily reliability without requiring file generation or manual intervention.

---

## Project Description

This automation runs **every day**, queries the latest dispatch data from a database, formats the summary inside UiPath, and opens WhatsApp Web to send the result as a chat message to a designated group or contact. No external Excel files or APIs are involved.

---

## Key Features

- Daily execution (can be scheduled via Orchestrator)
- Database data retrieval using `UiPath.Database.Activities`
- In-memory data processing (no Excel used)
- Message summary formatting directly in UiPath
- WhatsApp Web automation using UI-based selectors
- REFramework foundation for stability and error handling
- Screenshots and logs for monitoring and diagnostics

---

## Data Handling

The bot connects to a SQL database, processes Local Scrap dispatch data, and compiles metrics such as:

- Number of vehicles
- Number of transactions
- Net weight actual vs. theoretical
- Average process time (HH:mm)

The message is structured into a readable report and sent directly via WhatsApp Web.

---

## Project Structure

| Folder/File                    | Description                                                   |
|--------------------------------|---------------------------------------------------------------|
| Main.xaml                      | Main entry point for the automation                          |
| Modular/                       | Sub-workflows (e.g., WhatsAppSender, DBFetcher, Formatter)   |
| Framework/                     | REFramework components                                        |
| Data/Config.xlsx               | Configuration for DB connection, group name, etc.            |
| .local/                        | Internal UiPath system folder                                 |
| project.json                   | UiPath project metadata                                       |
| README.md                      | Project documentation                                         |

---

## Process Workflow

### 1. **Initialization**
- Load configuration from `Config.xlsx` (e.g., DB credentials, WA group name)
- Initialize system resources and variables

### 2. **Database Query**
- Use `UiPath.Database.Activities` to fetch Local Scrap data for the day

### 3. **Data Processing**
- Process metrics within UiPath:
  - Vehicle and transaction counts
  - Net weight comparison
  - Time averages

### 4. **Message Formatting**
- Construct a report string like:

