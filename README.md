# FastAPI Product Inventory Manager

A full-stack product inventory management system built with **FastAPI** (Python backend) and a **React** frontend. Supports full CRUD operations — create, read, update, and delete products — with data persisted in a **SQLite** database via SQLAlchemy.

---

## 📂 Project Structure

```
FASTAPI/
├── fastapi/                # (virtual environment — do not commit)
├── frontend/               # React frontend application
│   ├── node_modules/
│   ├── public/
│   ├── src/
│   ├── package.json
│   └── ...
├── .gitignore              # Git ignore rules
├── database_models.py      # SQLAlchemy ORM models (DB table definitions)
├── database.py             # Database engine & session configuration
├── main.py                 # FastAPI app — routes & endpoint logic
├── models.py               # Pydantic schemas (request/response validation)
└── README.md               # This file
```

---

## 🔧 Tech Stack

| Layer      | Technology                        |
|------------|-----------------------------------|
| Backend    | Python 3, FastAPI, Uvicorn        |
| ORM        | SQLAlchemy                        |
| Database   | SQLite                            |
| Validation | Pydantic                          |
| Frontend   | React, Axios                      |
| CORS       | FastAPI CORSMiddleware            |

---

## ⚙️ Backend Setup

### 1. Clone the repository

```bash
git clone https://github.com/VishnuSaiU/fastapi-demo.git
cd FASTAPI
```

### 2. Create & activate a virtual environment

```bash
# Windows
python -m venv fastapi
fastapi\Scripts\activate

# macOS / Linux
python -m venv fastapi
source fastapi/bin/activate
```

### 3. Install dependencies

```bash
pip install fastapi uvicorn sqlalchemy
```

> If you use Axios on the backend side for any proxy or utility, install it via npm in the frontend folder (see Frontend Setup).

### 4. Run the backend server

```bash
uvicorn main:app --reload
```

The API will be live at **http://127.0.0.1:8000**

You can explore the auto-generated docs at:
- Swagger UI → http://127.0.0.1:8000/docs
- ReDoc      → http://127.0.0.1:8000/redoc

---

## 🌐 Frontend Setup

```bash
cd frontend
npm install
npm start
```

The React app will start at **http://localhost:3000** and communicates with the FastAPI backend via CORS.

---

## 📦 API Endpoints

| Method | Endpoint              | Description                  |
|--------|-----------------------|------------------------------|
| GET    | `/products`           | Get all products             |
| GET    | `/products/{id}`      | Get a single product by ID   |
| POST   | `/products`           | Create a new product         |
| PUT    | `/products/{id}`      | Update an existing product   |
| DELETE | `/products/{id}`      | Delete a product by ID       |

---

## 🗂️ Key Files Explained

### `database.py`
Configures the SQLite database engine and creates a session factory (`SessionLocal`) using SQLAlchemy. Also exports the `Base` declarative base for all ORM models.

### `database_models.py`
Defines the SQLAlchemy ORM model (`Product`) that maps directly to the `products` table in SQLite. Columns typically include `id`, `name`, `description`, `price`, and `quantity`.

### `models.py`
Pydantic schemas used by FastAPI for **request validation** and **response serialization**. Keeps the API contract clean and separate from the database layer.

### `main.py`
The core FastAPI application. Includes:
- CORS middleware configuration (allows the React frontend to call the API)
- Database table creation on startup
- All CRUD route handlers using SQLAlchemy sessions

---

## 📝 Notes

- The SQLite database file (`database.db` or similar) is auto-created when the backend starts for the first time.
- The frontend is a standard Create React App project — no modifications were made to it.
- This project is based on the [navinreddy20/fastapi-demo](https://github.com/navinreddy20/fastapi-demo) reference (products-with-ui branch).