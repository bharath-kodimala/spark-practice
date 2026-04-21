Summary
This Databricks notebook demonstrates SCD-2 (Slowly Changing Dimension Type 2) implementation using SQL. SCD-2 maintains historical data by tracking changes over time with effective date ranges.

Key Steps:
Create Active Employee Table (employ_active)

Schema: employ_id, emp_address, active_state, start_date, end_date
Stores historical employee data with active status
Create Update Table (employ_update)

Schema: employ_id, emp_address
Contains new/updated employee records to process
Prepare Source Data

Adds required columns to the update table (active_state='Y', start_date=current_date, end_date='2199-01-01')
Creates two datasets:
New employees: margeID populated (for INSERT)
Existing employees: margeID=NULL (detected via EXISTS subquery)
UNION Both Datasets

Combines new and existing employee records into a single source
MERGE Operation (SCD-2 Logic)

MATCHED records: Updates existing employee rows by setting active_state='N' and end_date=current_date (marks old record as inactive)
NOT MATCHED records: Inserts new employee records with active_state='Y' and future end_date
Verification

Queries the final employ_active table sorted by active_state and employ_id
This approach maintains a complete audit trail while keeping the current active record easily accessible.
