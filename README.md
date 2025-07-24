# Montreal-Property-Report

This project generates and emails detailed real estate investment reports for residential properties in Montreal, based 
on user-submitted addresses. Reports are data-driven and enriched with AI-generated insights.


## Features
- Historical price trends and area comparisons
- Rent-to-price yield and appreciation analysis
- Basic price forecasting model
- PDF report generation
- Email delivery to user
- GPT-powered summary and recommendation


## Stack
- **Backend**: Java Spring Boot (REST API)
- **Data Pipeline**: Python (scraping, processing, ML, PDF)
- **Database**: PostgreSQL
- **AI Layer**: OpenAI GPT-4
- **Frontend**: (Optional) basic UI via Cursor/React/HTML


## How it Works
1. User submits an address and email.
2. The backend triggers the Python pipeline.
3. Data is collected, analyzed, and formatted into a report.
4. GPT adds a summary and investment recommendation.
5. Final PDF is emailed to the user.


## Getting Started
1. Clone the repo
2. Set up `.env` with OpenAI and SMTP credentials
3. Run backend: `cd backend && ./mvnw spring-boot:run`
4. Run Python pipeline: `cd pipeline && source venv/bin/activate`
