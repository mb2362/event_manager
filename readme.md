# 🧪 FastAPI Test Suite

This repository contains a FastAPI application with an asynchronous test suite using **Pytest**, **HTTPX**, and **SQLAlchemy**. The suite includes support for user authentication, role-based access control, and email service mocking.

## ✅ Key Features

- Asynchronous testing with `pytest-asyncio`
- Mocked services (e.g., email) using `AsyncMock`
- Role-based access fixtures (e.g., admin, manager, regular user)
- JWT-based authentication with reusable fixtures
- Isolated test database setup
- Coverage-friendly and CI-ready with GitHub Actions

---

## 🐛 Workflow Not Triggering on Push?

If your GitHub Actions workflow doesn't run when you push to `main`, make sure your workflow file includes the correct trigger.

### ✅ To Trigger the Workflow

**Option 1: Make a Commit to main**
- Edit any file in your forked repo (even just add a space).
- Commit the change directly to `main`.
- That will trigger the workflow automatically!

**Option 2: Open a Pull Request**
- Create a new branch.
- Make a small change and push it.
- Open a pull request into `main` — this will also trigger the workflow.

**Option 3: Add `workflow_dispatch` to Trigger Manually**
If you want to trigger it manually from the Actions tab, just add this at the top under `on:`:

```yaml
on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
  workflow_dispatch:  # 👈 Add this line
```

Then commit this change. You’ll now see a **"Run workflow"** button in the Actions tab.


## 💻 Environment

| Tool              | Version         |
|-------------------|------------------|
| OS                | Ubuntu 22.04     |
| Python            | 3.10.12          |
| Pytest            | 8.1.1            |
| FastAPI           | 0.110.0          |
| SQLAlchemy        | 2.0.29           |
| httpx             | 0.27.0           |
| pytest-asyncio    | 0.23.6           |
| alembic           | 1.13.1           |
| uvicorn           | 0.29.0           |
| bcrypt            | 4.1.2            |
| email-validator   | 2.1.1            |
| python-jose       | 3.3.0            |
| asyncpg           | 0.29.0           |
| aiomysql          | 0.2.0            |
| PyMySQL           | 1.1.0            |
| gunicorn          | 21.2.0           |
| coverage          | 7.4.4            |
| factory-boy       | 3.3.0            |
| Faker             | 24.4.0           |

---

## 📬 Contact

For issues, suggestions, or contributions, feel free to open an Issue or submit a PR.