# Expense Tracker

A lightweight full-stack personal finance application built as part of an assignment. It allows users to record, view, and manage expenses with a focus on simplicity and reliability.

---

## Features

* Create and track expenses
* Idempotent API to prevent duplicate entries during retries
* Filter and sort expenses
* FastAPI backend with RESTful design
* Streamlit frontend
* SQLite database for persistence
* Automated testing using pytest
* Input validation and error handling

---

## Tech Stack

* Backend: FastAPI
* Frontend: Streamlit
* Database: SQLite
* Testing: Pytest

---

## Project Structure

Expense-Tracker/
│
├── backend/
│   └── main.py
├── data/
│   └── expenses.db
├── streamlit_app.py
├── requirements.txt
├── start_app.bat
└── tests/

---

## Setup and Run Locally

1. Install dependencies
   pip install -r requirements.txt

2. Start the backend server
   uvicorn backend.main:app --reload

3. Run the frontend
   streamlit run streamlit_app.py

On Windows, you can use `start_app.bat` to run both services together.

---

## Default Configuration

* Backend API: http://127.0.0.1:8000
* Database file: data/expenses.db

---

## API Documentation

### POST /expenses

Creates a new expense.

Example request:
{
"amount": "125.50",
"category": "Food",
"description": "Lunch",
"date": "2026-04-29"
}

Idempotency support:

* Use an `Idempotency-Key` header
* Same key with same payload returns the existing record
* Same key with different payload returns 409 Conflict

---

### GET /expenses

Retrieves expenses.

Optional query parameters:

* category=Food
* sort=date_desc

---

## Running Tests

pytest

Test coverage includes:

* Expense creation
* Expense retrieval
* Category filtering
* Sorting by date
* Amount validation
* Idempotent request handling

---

## Design Decisions

* SQLite is used for simplicity and persistence

* Monetary values are stored as integer paise (amount_minor) to avoid floating point errors

* API responses return formatted values as rupee strings with two decimal places

* Idempotency-Key support ensures:

  * Safe retries
  * No duplicate entries
  * Reliable behavior in case of refresh or network delays

---

## Trade-offs and Limitations

* No authentication or user accounts

* No pagination

* No recurring expense support

* No advanced UI framework

* UI is built using basic Streamlit components

* Category filtering is based on exact matches

---

## Live Demo


https://fenmo-assignment-sz8k8j7szqstr6lqqqzqcl.streamlit.app/
---

## Future Improvements

* Add authentication and user management
* Implement pagination and search
* Support recurring expenses
* Improve UI/UX
* Add containerization and CI/CD

---

## Contributing

This project is part of an assignment. Suggestions and improvements are welcome.

---

## License

This project is for educational purposes.
