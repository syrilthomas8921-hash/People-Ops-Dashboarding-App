People Ops: Workforce Insights
A privacy-first HR analytics dashboard that runs entirely in your browser.
Upload your employee and hiring data as CSV files and instantly get workforce KPIs, charts, and a downloadable PDF report — no account, no server, no data ever leaves your device.

Table of Contents
What This App Does
Getting Started
How to Use the App
Preparing Your CSV Files
Pages Explained
Exporting Reports
Filtering Data
Frequently Asked Questions
For Developers
What This App Does
People Ops: Workforce Insights is a dashboard for HR and People Operations teams. It takes your existing employee and hiring data — exported as CSV files from any HR system — and turns it into:

Live KPI cards (headcount, attrition, absence, overtime cost, time-to-hire)
Interactive charts you can click to filter
A data quality report that flags missing or incorrect records
A downloadable PDF workforce report
CSV exports of all computed metrics
Everything runs in your browser. You do not need to create an account. Your data is never uploaded to a server.

Getting Started
Step 1 — Make sure you have Node.js installed
Go to https://nodejs.org and download the LTS version if you do not already have it.

To check if it is installed, open Command Prompt and type:


node -v
You should see a version number. If you do, you are ready.

Step 2 — Download the project
Download or clone this repository to your computer. If you downloaded a ZIP file, extract it to a folder of your choice.

Step 3 — Open Command Prompt and navigate to the project folder

cd /d "d:\path\to\people-ops-workforce-insights"
Replace the path with wherever you extracted the project.

Step 4 — Install dependencies
This only needs to be done once:


npm install
Wait for it to finish. You will see a node_modules folder appear.

Step 5 — Start the app

npm run dev
You will see something like:


  VITE ready in 400ms

  Local:   http://localhost:5173/
Open http://localhost:5173 in your browser and the app will load.

The app comes with built-in sample data so you can explore every feature before uploading your own files.

How to Use the App
First time — explore with sample data
When you first open the app you will see a banner saying Showing built-in sample data. This is intentional. You can click through every page, see how the charts look, and try the filters before touching your real data.

Uploading your own data
Click the Upload CSV button in the top navigation bar
A panel will slide in from the right
You will see three upload slots:
Employee Records — required
Hiring Pipeline — optional
Monthly Snapshot — optional (needed for trend charts)
Click Choose file next to each slot and select your CSV
The app will validate your file and show any errors or warnings
Once you are happy, click Load Data
Your data will populate all six pages immediately.

If you do not have a hiring or snapshot file yet, you can upload just the employee file and still get meaningful insights.

Switching back to sample data
If you want to go back to the sample data at any time, refresh the page. Your uploaded data is held in memory only and is cleared when you close or refresh the browser tab.

Preparing Your CSV Files
Your CSV files need to have specific column names for the app to read them correctly. The easiest way to get the right format is to download the templates from inside the app:

Click Upload CSV
Next to each slot you will see a Download template link
Open the template in Excel or Google Sheets
Fill in your data using the same column headers
Export as CSV and upload
Employee Records — required columns
These columns must be present. The app will reject the file if any are missing.

Column name	What to put here	Example
Employee_ID	Unique ID for each employee	EMP-001
Full_Name	Employee full name	Jane Smith
Department	Department name	Engineering
Job_Title	Job title	Senior Developer
Location	Office or city	London
Contract_Type	Permanent, Fixed-Term, Contractor, or Part-Time	Permanent
Employment_Status	Active, Terminated, or On Leave	Active
Hire_Date	Date joined in YYYY-MM-DD format	2022-03-15
Salary_Band	Salary band label	Band 3
Monthly_Salary	Monthly gross salary in GBP	4500
These columns are optional but recommended:

Column name	What to put here
Exit_Date	Date left in YYYY-MM-DD format — leave blank if still employed
Manager	Name of direct manager
Monthly_Absence_Days	Number of absence days in the month
Overtime_Hours	Overtime hours worked in the month
Gender_optional	Gender — leave blank if not collected
Date_of_Birth_optional	Date of birth in YYYY-MM-DD format
Hiring Pipeline — optional columns
Column name	What to put here	Example
Role_ID	Unique ID for the role	REQ-001
Role_Title	Job title being hired for	Product Manager
Department	Hiring department	Product
Open_Date	Date role was opened in YYYY-MM-DD	2025-01-10
Stage	Current pipeline stage	Interview
Status	Open, On Hold, Filled, or Cancelled	Open
Candidate_Count	Number of active candidates	4
Expected_Close_Date	Target close date in YYYY-MM-DD	2025-04-30
Hiring_Manager	Name of the hiring manager	John Davies
Monthly Snapshot — optional columns
This file enables the trend charts on the Overview and Time pages. It should have one row per department per month, plus one row with Department set to All for the overall totals.

Column name	What to put here	Example
Month	Year and month in YYYY-MM format	2025-03
Department	Department name or All for totals	All
Headcount	Total headcount at end of month	142
Joiners	Number of joiners in the month	3
Leavers	Number of leavers in the month	1
Absence_Days	Total absence days in the month	48
Overtime_Hours	Total overtime hours in the month	210
Overtime_Cost	Estimated overtime cost in GBP	8400
Pages Explained
Overview
The main dashboard. Shows six KPI cards at the top — headcount, joiners, leavers, attrition rate, average absence days, and open roles. Below are five charts: headcount trend over time, department split, joiners vs leavers trend, contract type mix, and headcount by location.

Tip: Click any slice on the Department Split pie chart to filter the whole page by that department.

Data Quality
Runs an automatic check on your employee data and flags any issues it finds. Six checks are performed:

Check	What it looks for
Duplicate IDs	Two or more employees with the same Employee_ID
Missing required fields	Rows where a required column is blank
Invalid dates	Dates that are not in the expected YYYY-MM-DD format
Zero salary — active	Active employees recorded with a monthly salary of zero
Missing exit date	Terminated employees with no Exit_Date recorded
Missing manager	Employees with no Manager assigned
Each check shows a pass, warning, or error result with the number of affected records and an example. Use this page to clean your data before running reports.

Workforce Metrics
Deep-dive headcount analytics. Includes headcount by department, contract type distribution, tenure bucket breakdown, gender split, attrition trend over time, and a full department summary table showing joiners, leavers, net change, and attrition percentage per department.

Time and Compensation
Absence and overtime analytics. Shows total absence days, average absence per employee benchmarked against 2 days, total overtime hours, and estimated overtime cost calculated at 1.5x the average hourly rate. Includes a high-absence employee table and absence and overtime breakdowns by department. Salary band distribution is also shown here.

Hiring Snapshot
Full hiring pipeline view. KPI cards show open roles, total candidates in pipeline, hires made in the selected month, and estimated average time-to-hire. Below is a pipeline funnel by stage, open roles by department, and a detailed table of every role with its stage, status, candidate count, and expected close date.

Export Summary
Configure and download the monthly workforce report. See the Exporting Reports section below for full instructions.

Exporting Reports
PDF Report
Go to Export Summary in the left navigation
Enter your organisation name in the settings panel at the top
Select which sections to include by clicking the checkboxes
Click PDF Summary
The PDF will download automatically to your downloads folder
The PDF includes a branded cover page with your organisation name and the report period, followed by one page per selected section with KPI blocks, tables, and page numbers throughout.

CSV Data Pack
Go to Export Summary
Click CSV Data Pack
Four CSV files will download in sequence:
kpi-summary-YYYY-MM.csv — all KPI metrics as a flat table
dept-breakdown-YYYY-MM.csv — headcount by department
employee-records.csv — full employee dataset
hiring-pipeline.csv — full hiring dataset
You can also download each file individually using the buttons in the Individual exports section.

Filtering Data
Every page except Export Summary has a filter bar at the top. You can filter by multiple criteria at once.

To apply a filter:

Click one of the filter buttons (Department, Contract Type, Location, etc.)
A dropdown will appear with a list of values
Check the values you want to include
Click anywhere outside the dropdown to close it
The page updates immediately
Active filters appear as chips below the filter buttons showing which values are selected. Click the X on any chip to remove that filter.

To clear all filters click the Clear all button that appears when any filter is active.

Filters persist as you navigate between pages. If you apply a department filter on Overview it will still be applied when you go to Workforce Metrics. This is intentional so you can explore a subset of your workforce across all views.

Frequently Asked Questions
Is my data safe?
Yes. Your CSV files are read directly by your browser and never sent anywhere. No internet connection is required once the app is running. Closing the browser tab removes all data from memory.

What happens if I upload a file with the wrong columns?
The app will show a validation error listing the missing columns before loading the data. Nothing will be overwritten until you click Load Data on a valid file.

Can I use this with data from any HR system?
Yes, as long as you can export a CSV from your system and rename the columns to match the expected names. Most HR systems (BambooHR, Workday, HiBob, Personio, etc.) support CSV exports.

Why are the trend charts empty?
Trend charts require the Monthly Snapshot file. If you only uploaded the Employee Records file, trend charts will not have historical data to display. The current month KPIs will still be accurate.

Can multiple people use this at the same time?
Not in the same session. Each person runs their own local copy in their own browser. There is no shared database or real-time collaboration.

My data disappears when I refresh the page — is that a bug?
No, this is by design. Keeping data in memory only means it cannot be accessed by other browser tabs, extensions, or anyone else who uses the computer after you. Re-upload your CSV after refreshing to restore your data.

For Developers
Tech stack
React 18, Vite, Tailwind CSS, React Router v6 (HashRouter), Recharts, PapaParse, jsPDF, jspdf-autotable, date-fns, Lucide React.

Project structure

src/
  charts/          Recharts chart components
  components/      Reusable UI components (FilterBar, Sidebar, UploadModal, etc.)
  config/          Data model field definitions and KPI configuration
  context/         DataContext — global state for employees, hiring, filters
  data/            Built-in mock data for sample mode
  hooks/           useFilteredEmployees, useFilteredHiring, useEmployeeOptions
  layouts/         AppLayout — sidebar, header, page shell
  pages/           One file per page (Overview, DataQuality, etc.)
  utils/           KPI formulas, CSV parser, PDF export, CSV export, date helpers
Available scripts
Command	What it does
npm run dev	Start local development server at http://localhost:5173
npm run build	Build optimised production files to dist/
npm run preview	Preview the production build locally
Deploying
The dist/ folder produced by npm run build is a fully static site. Deploy it to Netlify, Vercel, GitHub Pages, or any web server that can serve static files. No server-side configuration is required.

License
MIT
