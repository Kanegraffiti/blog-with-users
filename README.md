# Blog with Users

Blog with Users is a Flask-powered multi-author blogging platform that supports user registration, authentication, and rich text content creation. The application demonstrates how to combine Flask extensions such as Flask-Login, Flask-Bootstrap, and Flask-CKEditor to build a full-featured blog with a modern UI, protected admin routes, and threaded comments.

## Features

- **Rich text posts** – Authors can compose blog entries with formatted content and feature images using CKEditor.
- **User accounts** – Visitors can register, log in, and leave comments on posts.
- **Admin controls** – The first registered user (ID 1) has access to create, edit, and delete posts.
- **Commenting system** – Authenticated users can discuss each post with CKEditor-powered comments.
- **SQLite persistence** – Data is stored in a local SQLite database by default, or you can provide a custom database URL.

## Project structure

```
.
├── main.py          # Flask application entry point and route definitions
├── forms.py         # WTForms definitions for posts, login, registration, and comments
├── templates/       # Jinja2 templates for pages and partials
├── static/          # Static assets (CSS, JS, images)
├── requirements.txt # Python dependencies for pip users
└── Procfile         # Production process file (e.g., for Heroku)
```

## Prerequisites

- Python 3.8+
- pip (or Poetry if you prefer managing dependencies via `pyproject.toml`)

## Local setup

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd blog-with-users
   ```

2. **Create and activate a virtual environment** (recommended)

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   > Alternatively, install with Poetry:
   >
   > ```bash
   > poetry install
   > ```

4. **Configure environment variables** (optional)

   The application will fall back to sensible defaults, but you can customize them:

   - `SECRET_KEY` – Flask session secret (defaults to `dev-secret-key`).
   - `DATABASE_URL` – SQLAlchemy database URI (defaults to `sqlite:///blog.db`).

   On macOS/Linux:

   ```bash
   export SECRET_KEY="choose-a-secret"
   export DATABASE_URL="sqlite:///blog.db"
   ```

   On Windows PowerShell:

   ```powershell
   $env:SECRET_KEY = "choose-a-secret"
   $env:DATABASE_URL = "sqlite:///blog.db"
   ```

5. **Initialize the database**

   The app will automatically create the necessary tables when it starts. If you are using the included `blog.db`, no additional work is required.

6. **Run the development server**

   ```bash
   python main.py
   ```

   The server listens on http://127.0.0.1:5000/ by default. Open the URL in your browser to explore the blog.

7. **Create an admin account**

   Register a new user from the UI. The first user stored in the database (ID 1) receives admin privileges and can create, edit, and delete posts.

## Deployment

A `Procfile` is provided for hosting on platforms such as Heroku using Gunicorn:

```
web: gunicorn main:app
```

Be sure to set the same environment variables (`SECRET_KEY`, `DATABASE_URL`) in your hosting environment.

## License

This project is provided as-is for demonstration purposes.
