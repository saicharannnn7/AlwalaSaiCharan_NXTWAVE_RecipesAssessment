# AlwalaSaiCharan_NXTWAVE_RecipesAssessment
saicharannnn7/receipe

Recipe Recipes Project

This is a recipe management application with a *FastAPI backend* and a frontend (to be set up separately).  
The backend uses *PostgreSQL* as the database.  

---

How to Run the Backend (Step by Step)

1. Clone the Repository
cmd
git clone <your-repo-url>
cd recipe-recipes-project\backend

2. Create a Virtual Environment
python -m venv .venv

3. Activate the Virtual Environment (Command Prompt)
.venv\Scripts\activate

4. Install Dependencies
pip install -r requirements.txt

🗄 PostgreSQL Database Setup
1. Install PostgreSQL

Download from https://www.postgresql.org/download/

During setup, note down:

username (default = postgres)

password

port (default = 5432)

2. Create a Database

Open psql (PostgreSQL shell) and run:

CREATE DATABASE recipe_db;
CREATE USER recipe_user WITH PASSWORD 'recipe_password';
ALTER ROLE recipe_user SET client_encoding TO 'utf8';
ALTER ROLE recipe_user SET default_transaction_isolation TO 'read committed';
ALTER ROLE recipe_user SET timezone TO 'UTC';
GRANT ALL PRIVILEGES ON DATABASE recipe_db TO recipe_user;

3. Configure Environment Variables

Copy the example file:

copy .env.example .env


Open .env and update with your database details:

DATABASE_URL=postgresql://recipe_user:recipe_password@localhost:5432/recipe_db

4. Run Migrations (if any)

If Alembic or SQL scripts are provided, run them.
Example with SQL scripts in sql/:

psql -U recipe_user -d recipe_db -f sql/schema.sql

Run the FastAPI Server

Run this inside the backend folder:

uvicorn app.main:app --reload


If successful, you’ll see:

Uvicorn running on http://127.0.0.1:8000

Access the API

Root: http://127.0.0.1:8000

Swagger UI (Interactive Docs): http://127.0.0.1:8000/docs

ReDoc: http://127.0.0.1:8000/redoc

Project Structure
backend/
│── app/              # FastAPI application code
│   ├── main.py       # Entry point of the backend
│   ├── models.py     # Database models
│   ├── routers/      # API endpoints
│   └── ...
│── sql/              # SQL schema & data
│── load_data.py      # Script to load sample data
│── requirements.txt  # Python dependencies
│── .env.example      # Example environment variables

🛠 Useful Commands
Install new dependency
pip install package_name
pip freeze > requirements.txt

Deactivate virtual environment
deactivate
