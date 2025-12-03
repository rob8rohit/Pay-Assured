PayAssured – Invoice Recovery Case Tracker

Full Stack Internship Assignment Submission
Tech Stack: FastAPI (Python), Express.js (Node), HTML/JS, PostgreSQL/MySQL

📌 Project Overview

This project is a mini internal CRM system that PayAssured can use to track:

Clients

Their unpaid invoices

Recovery follow-up progress

The system includes a Python FastAPI backend, Node.js Express frontend, and a relational database schema.

📁 Project Structure
payassured_assignment/
│── backend/                     # FastAPI backend
│    ├── app/
│    │    ├── routers/           # API routes
│    │    ├── models.py          # SQLAlchemy models
│    │    ├── schemas.py         # Pydantic schemas
│    │    ├── crud.py            # Database operations
│    │    ├── db.py              # DB connection setup
│    │    └── main.py            # FastAPI entrypoint
│    ├── requirements.txt
│── frontend/                    # Node.js frontend
│    ├── public/
│    │     ├── index.html        # Case list page
│    │     ├── case_create.html  # Create case page
│    │     └── case_detail.html  # Case details page
│    ├── server.js               # Express server
│    └── package.json
│── db/
│    └── schema.sql              # Database schema
│── screenshots/                 # Required screenshots
│── .env.example                 # Environment config example
│── README.md

⚙️ Backend Setup (FastAPI – Python)
1. Create Virtual Environment & Install Dependencies
cd backend
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt

2. Environment Variables

Create a .env file inside /backend:

DATABASE_URL=postgresql+psycopg2://postgres:password@localhost:5432/payassured_dev


Or use MySQL:

DATABASE_URL=mysql+pymysql://root:password@localhost/payassured_dev

3. Run Backend Server
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000


Backend will run at:

👉 http://localhost:8000

👉 API Docs (Swagger): http://localhost:8000/docs

🧪 API Endpoints
Clients
Method	Endpoint	Description
POST	/clients	Create client
GET	/clients	List all clients
Cases
Method	Endpoint	Description
POST	/cases	Create case
GET	/cases	List cases (filter + sorting)
GET	/cases/{id}	Get case by ID
PATCH	/cases/{id}	Update status or notes
🖥️ Frontend Setup (Node.js – Express)
1. Install Dependencies
cd frontend
npm install

2. Run Frontend
node server.js


Frontend available at:
👉 http://localhost:3000

📄 Frontend Pages
1. Case List Page (index.html)

Displays:

Client ID

Invoice Number

Amount

Due Date

Status

Sorting & Filtering

2. Case Create Page (case_create.html)

Form to create a new case:

Client ID

Invoice number

Amount

Invoice date

Due date

3. Case Detail Page (case_detail.html)

Shows:

All case fields

Update status

Update follow-up notes

🗄 Database Schema

Located in /db/schema.sql

📌 clients table
id (PK)
client_name
company_name
city
contact_person
phone
email

📌 cases table
id (PK)
client_id (FK → clients.id)
invoice_number
invoice_amount
invoice_date
due_date
status
last_follow_up_notes
created_at
updated_at

📷 Screenshots

The screenshots/ folder contains required screenshots:

Case List Page

Case Detail Page

Case Create Page

(Placeholder generated.)

🚀 How to Run Full Project

Start backend:

uvicorn app.main:app --reload


Start frontend:

node server.js


Ensure your DB server is running and schema is created:

psql / mysql < db/schema.sql

📌 Notes

FastAPI auto-generates API docs.

SQLAlchemy used for ORM.

Express serves static HTML pages.

Fully compatible with PostgreSQL or MySQL.
