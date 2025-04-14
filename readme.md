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

## 🚮 [Bug] test_user_schema: First name and nickname validation

### Describe the Bug
`test_user_schema` failed due to missing or invalid `first_name` and `nickname` fields in the schema definition or test data.

### Suggested Fix
Ensure the schema includes optional/required `first_name` and `nickname` fields where expected. Tests should provide valid mock values.

### Resolution
This issue was resolved by providing appropriate values for these fields in the schema or marking them as optional.

Resolved and closed in [#1](https://github.com/mb2362/event_manager/tree/1-test-test_user_schema-fixed-first-name-nickname-errors).

### Final Fix (Fixtures Updated)
```python
@pytest.fixture
def user_base_data_invalid():
    return {
        "username": "john_doe_123",
        "email": "john.doe.example.com",
        "full_name": "John Doe",
        "bio": "I am a software engineer with over 5 years of experience.",
        "profile_picture_url": "https://example.com/profile_pictures/john_doe.jpg"
    }

@pytest.fixture
def user_create_data(user_base_data):
    return {**user_base_data, "password": "SecurePassword123!"}

@pytest.fixture
def user_update_data():
    return {
        "email": "john.doe.new@example.com",
        "full_name": "John H. Doe",
        "bio": "I specialize in backend development with Python and Node.js.",
        "profile_picture_url": "https://example.com/profile_pictures/john_doe_updated.jpg",
        "nickname": "manager_john",
        "first_name": "John",
    }
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