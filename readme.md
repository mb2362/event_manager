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

## ❌ [Bug] USER,LOGIN Validation Error

### Describe the Bug
Validation failed in schema tests for both `UserResponse` and `LoginRequest`. These are caused by incorrect or incomplete model definitions used in test cases.

### To Reproduce

1. Run tests in `tests/test_schemas/test_user_schemas.py`
2. See failure:
   - `test_user_response_valid` fails with `pydantic_core.ValidationError`
   - `test_login_request_valid` fails with `pydantic_core.ValidationError`

### Expected Behavior
Both schema tests should pass with valid example data.

### Suggested Fix
Ensure required fields in `UserResponse` and `LoginRequest` are populated with valid mock data. Check types and default values in your Pydantic models.

### Resolution
This issue was resolved and merged in [#2](https://github.com/mb2362/event_manager/tree/2-test-userlogin-validation-error). The fix involved updating the schema tests to provide correct mock data.

### Final Fix (Fixtures Updated)
```python
@pytest.fixture
def user_response_data():
    return {
        "id": uuid4(),  # Real UUID object
        "username": "testuser",
        "email": "test@example.com",
        "last_login_at": datetime.now(),
        "created_at": datetime.now(),
        "updated_at": datetime.now(),
        "links": [{"rel": "self", "href": "/users/testuser"}]  # Provide minimal valid structure if expected
    }

@pytest.fixture
def login_request_data():
    return {"email": "john.doe@example.com", "password": "SecurePassword123!"}  # was "username"
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