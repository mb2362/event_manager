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

## 🔧 Test Setup

Make sure to install development dependencies:

```bash
pip install -r requirements.txt
```

To run tests:

```bash
pytest
```

To run tests with coverage:

```bash
pytest --cov=app tests/
```

---

## 🔐 Authentication Fixture: `admin_token`

Some tests depend on an admin-authenticated context provided by a reusable `admin_token` fixture.

### Example Fixture (in `conftest.py`):

```python
# conftest.py
import pytest
from app.core.auth import create_access_token

@pytest.fixture
async def admin_token(admin_user):
    token = create_access_token(data={"sub": str(admin_user.id), "role": admin_user.role})
    return token
```

This fixture enables authenticated requests on admin-only endpoints.

---

## 📁 Directory Structure

```text
.
├── app/                    # FastAPI application code
├── email_templates/
├── nginx/
├── settings/
├── tests/                 # All test modules
│   ├── test_api/
│   │   └── test_users_api.py
│   ├── test_models/
│   ├── test_schemas/
│   │   └── test_user_schemas.py
│   ├── test_services/
│   ├── conftest.py
│   ├── test_conftest.py
│   ├── test_email.py
│   ├── test_link_generation.py
│   ├── test_security.py
├── venv/
├── .env.sample
├── alembic.ini
├── docker-compose.yml
├── Dockerfile
├── logging.conf
├── pytest.ini
├── readme.md
├── requirements.txt
└── ...
```

---

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