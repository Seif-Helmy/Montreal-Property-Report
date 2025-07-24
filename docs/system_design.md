# System Design: Montreal Property Intelligence Report

## Overview
This system generates property intelligence reports focused on the Montreal real estate market. 
It combines historical data, forecasting, and natural language summaries.


## Architecture
- **User Input**: Address + email via REST API
- **Spring Boot Backend**:
    - Accepts and validates input
    - Triggers pipeline job
- **Python Pipeline**:
    - Fetches and preprocesses data
    - Generates Markdown report
    - Calls GPT API for summary
    - Converts to PDF
    - Sends report via email
- **PostgreSQL**: Stores processed properties and cached area metrics


## Modules

### Backend (`backend/`)
- `ReportController.java`: accepts user requests
- `JobService.java`: triggers and manages the pipeline call

### Pipeline (`pipeline/app/`)
- `data_fetcher.py`: gets sale, rent, trend data
- `report_generator.py`: formats Markdown + plots
- `summary_writer.py`: sends report to GPT
- `emailer.py`: sends report to user
- `utils/`: helper scripts (geo, model, file)


## Flow Diagram
[User] → [Spring Boot API] → [Python Pipeline] → [GPT API + PDF Gen] → [Email to User]


## Data Sources
- Centris.ca / Realtor.ca (scraped)
- CMHC + StatCan CSVs
- OpenStreetMap (geolocation)
- Kaggle datasets (historical)


## Security
- API keys loaded from `.env`
- `.env` is excluded from Git via `.gitignore`
- SMTP auth uses app-specific passwords
