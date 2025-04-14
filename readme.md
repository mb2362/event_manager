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

## 🔐 Authentication Fixtures

Some tests depend on authenticated user contexts provided by reusable fixtures like `user_token`, `admin_token`, and `manager_token`.

### Manager Token Fixture (in `conftest.py`):

```python
# conftest.py
import pytest
from app.core.security import create_access_token

@pytest.fixture
async def manager_token(manager_user):
    token = create_access_token(data={"sub": str(manager_user.id), "role": manager_user.role.name})
    return token
```

This fixture allows tests to simulate authenticated requests from a manager user and is essential for testing role-based access control.

---

## 📁 Directory Structure

```text
.
├── app/                    # FastAPI application code
├── tests/                  # All test modules
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
│   └── test_security.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── readme.md
```

---

## 🤫 Example Usage of `manager_token`

```python
async def test_list_users_as_manager(async_client, manager_token):
    response = await async_client.get(
        "/users/",
        headers={"Authorization": f"Bearer {manager_token}"}
    )
    assert response.status_code == 200
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

## 🧹 Additional Notes

- If you encounter `FixtureNotFound` errors, ensure all relevant fixtures like `manager_token` are defined in `conftest.py`.
- Tests requiring roles (e.g., manager) should use dedicated fixtures like `manager_user` and `manager_token`.
- Mocks for third-party services (e.g., email) are injected using `AsyncMock` to ensure isolation and testability.

---

## 📬 Contact

For issues, suggestions, or contributions, feel free to open an Issue or submit a PR.