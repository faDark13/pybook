# Django Project Setup Guide

A standard, step-by-step guide to setting up and running this Python/Django project using a Python virtual environment (`venv`).

---

## Prerequisites

Ensure you have the following installed on your system:
- **Python 3.10+** (Python 3.8+ minimum supported)
- **pip** (Python package manager)
- **Git**

You can verify your Python and pip installation by running:

```bash
python3 --version
pip --version
```
*(On Windows, you may need to use `python` instead of `python3`)*

---

## Getting Started with `venv`

### 1. Clone or Open the Project

Navigate to your project root directory:

```bash
cd /path/to/your-project
```

---

### 2. Create the Virtual Environment

Create a virtual environment named `.venv` (or `venv`):

```bash
# macOS / Linux
python3 -m venv .venv

# Windows
python -m venv .venv
```

> **Tip:** Naming the directory `.venv` keeps it hidden on Unix systems and is automatically recognized by editors like VS Code and PyCharm.

---

### 3. Activate the Virtual Environment

Activate the environment before installing dependencies or running commands:

- **macOS / Linux (Bash/Zsh):**
  ```bash
  source .venv/bin/activate
  ```

- **Windows (Command Prompt):**
  ```cmd
  .venv\Scripts\activate.bat
  ```

- **Windows (PowerShell):**
  ```powershell
  .venv\Scripts\Activate.ps1
  ```
  *(If you encounter a script execution policy error on PowerShell, run `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`)*

- **Fish Shell:**
  ```fish
  source .venv/bin/activate.fish
  ```

> When active, your terminal prompt will be prefixed with `(.venv)`.

---

### 4. Upgrade pip and Install Dependencies

With the virtual environment activated:

```bash
# Upgrade pip
python -m pip install --upgrade pip

# Install project dependencies
pip install -r requirements.txt
```

*(If you don't have a `requirements.txt` yet, you can install Django and freeze requirements)*:
```bash
pip install django
pip freeze > requirements.txt
```

---

### 5. Configure Environment Variables (Optional)

If your project uses a `.env` file for configuration (e.g. with `python-dotenv` or `django-environ`):

```bash
cp .env.example .env
```
Update `.env` with your secret key, database credentials, and debug settings.

---

### 6. Run Database Migrations

Apply database migrations:

```bash
python manage.py migrate
```

Create an administrative user (optional):

```bash
python manage.py createsuperuser
```

---

### 7. Start the Development Server

Run the Django local development server:

```bash
python manage.py runserver
```

Open your browser and navigate to:
[http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

### 8. Deactivate the Virtual Environment

When you are finished working on the project, deactivate the virtual environment:

```bash
deactivate
```

---

## Useful Commands Cheat Sheet

| Task | Command |
|---|---|
| **Activate venv (Linux/macOS)** | `source .venv/bin/activate` |
| **Activate venv (Windows)** | `.venv\Scripts\activate` |
| **Deactivate venv** | `deactivate` |
| **Install package** | `pip install <package_name>` |
| **Freeze dependencies** | `pip freeze > requirements.txt` |
| **Run migrations** | `python manage.py migrate` |
| **Create migrations** | `python manage.py makemigrations` |
| **Run dev server** | `python manage.py runserver` |
| **Run tests** | `python manage.py test` |
| **Access Django shell** | `python manage.py shell` |

---

## Git Best Practice

Never commit your virtual environment directory to version control. Ensure `.venv/` is included in your `.gitignore`:

```gitignore
# Virtual environment
.venv/
venv/
ENV/
env/

# Python cache
__pycache__/
*.py[cod]

# Django
*.log
local_settings.py
db.sqlite3
media/
```
