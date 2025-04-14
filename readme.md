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

Make sure to install dependencies:

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
│   ├── test_api/
│   │   └── test_users_api.py
│   ├── test_models/
│   ├── test_schemas/
│   │   └── test_user_schemas.py
│   ├── test_services/
│   ├── conftest.py         # Global test fixtures
│   ├── test_confest.py
│   ├── test_email.py
│   ├── test_link_generation.py
│   └── test_security.py
├── email_templates/
├── nginx/
├── settings/
├── requirements.txt
├── .env.sample
├── docker-compose.yml
├── Dockerfile
├── docker.md
├── git.md
├── license.txt
├── logging.conf
├── project_agile_req.md
├── project_structure.txt
├── pytest.ini
└── readme.md
```

---

## 🧪 Example Usage of `user_token`

```python
async def test_get_profile(client, user_token):
    response = await client.get("/users/me", headers={"Authorization": f"Bearer {user_token}"})
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
| aiofiles          | 23.2.1           |
| async-timeout     | 4.0.3            |
| asyncio           | 3.4.3            |
| cffi              | 1.16.0           |
| cryptography      | 42.0.5           |
| dnspython         | 2.6.1            |
| ecdsa             | 0.18.0           |
| exceptiongroup    | 1.2.0            |
| greenlet          | 3.0.3            |
| h11               | 0.14.0           |
| idna              | 3.6              |
| iniconfig         | 2.0.0            |
| Mako              | 1.3.2            |
| MarkupSafe        | 2.1.5            |
| packaging         | 24.0             |
| passlib           | 1.7.4            |
| pluggy            | 1.4.0            |
| psycopg           | 3.1.18           |
| psycopg2-binary   | 2.9.9            |
| pyasn1            | 0.6.0            |
| pycparser         | 2.22             |
| pydantic          | 2.6.4            |
| pydantic-settings | 2.2.1            |
| pydantic_core     | 2.16.3           |
| pypng             | 0.20220715.0     |
| python-dateutil   | 2.9.0.post0      |
| python-dotenv     | 1.0.1            |
| python-multipart  | 0.0.9            |
| qrcode            | 7.4.2            |
| rsa               | 4.9              |
| six               | 1.16.0           |
| sniffio           | 1.3.1            |
| starlette         | 0.36.3           |
| tomli             | 2.0.1            |
| typing_extensions | 4.10.0           |
| validators        | 0.24.0           |
| annotated-types   | 0.6.0            |
| async-sqlalchemy  | 1.0.0            |
| markdown2         | latest           |
| pyjwt             | latest           |

---

## 🧹 Additional Notes

- If you encounter `FixtureNotFound` errors, ensure all relevant fixtures are defined in `conftest.py`.
- Tests requiring roles (e.g., admin) should use dedicated fixtures like `admin_user` and `admin_token`.
- Mocks for third-party services (e.g., email) are injected using `AsyncMock` to ensure isolation and testability.

---

## 📬 Contact

For issues, suggestions, or contributions, feel free to open an Issue or submit a PR.