# 🧪 FastAPI Test Suite

This repository contains a FastAPI application with an asynchronous test suite using **Pytest**, **HTTPX**, and **SQLAlchemy**. The suite includes support for user authentication, role-based access control, and email service mocking.

## ✅ Key Features

- Asynchronous testing with `pytest-asyncio`
- Mocked services (e.g., email) using `AsyncMock`
- Role-based access fixtures (e.g., admin, manager)
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

## 🔐 Authentication Fixture

Some tests depend on an authenticated user context provided by a reusable `user_token` fixture.

### Example Fixture (in `conftest.py`):

```python
# conftest.py
import pytest

@pytest.fixture
async def user_token(user, generate_token):
    return generate_token(user)
```

This fixture ensures tests that simulate authenticated API calls have access to a valid JWT token.

---

## 📁 Directory Structure

```text
.
├── app/                    # FastAPI application code
├── tests/                  # All test modules
│   ├── __init__.py
│   ├── test_users.py
│   ├── test_auth.py
│   └── ...
├── conftest.py             # Global test fixtures
├── requirements.txt    # Dev dependencies
└── readme.md
```

---

## 🧪 Example Usage of `user_token`

```python
async def test_get_profile(client, user_token):
    response = await client.get("/users/", headers={"Authorization": f"Bearer {user_token}"})
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

- If you encounter `FixtureNotFound` errors, ensure all relevant fixtures are defined in `conftest.py`.
- Tests requiring roles (e.g., admin) should use dedicated fixtures like `admin_user` and `admin_token`.
- Mocks for third-party services (e.g., email) are injected using `AsyncMock` to ensure isolation and testability.

---

## 📬 Contact

For issues, suggestions, or contributions, feel free to open an Issue or submit a PR.